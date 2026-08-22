# THE FORGE — architecture

*Working title. The name is one constant (`SCHOOL_NAME`) and one folder rename;
change it whenever it's decided.*

A tutor that starts a kid wherever they actually are, works them upward for
years, explains **why** on every single miss, and keeps a record of the growth
that outlives the browser.

---

## 1. WHY THIS IS BUILT THE WAY IT IS

The brief, in the owner's words: *"a big thing about the teachers is they don't
spend the time and tell you why. If you don't know the why, then you don't
understand why to do it... thirty kids in a class... it's impossible."*

That gap is the product. A machine will explain the same thing forty times
without sighing, and it will never run out of patience at 9pm. Everything below
serves that.

**There is no language model inside this file, and there cannot be.** Every
game in this arcade is one self-contained HTML file with no server, no
dependencies and no API key — that is what makes them free, private, offline,
and impossible to break. An LLM would need a key sitting in a public website
for anyone to take. So "tutor" here means what SOLVE and TALLY already prove
out: **content generated on the fly, a ladder that measures and moves the
learner, and an explanation written for every rule.** That genuinely reads
them, places them, and pushes them. It is not a chatbot, and it does not need
to be one to do this job.

If a conversational tutor is ever wanted, that is a separate build with a small
server behind it. It is not a reason to delay this one.

## 2. THE THING THAT MAKES IT REACH TWELFTH GRADE

Third grade to twelfth is thousands of skills. Nobody hand-writes that. So the
unit of work is not a "level" — it is a **SKILL**, and skills form a graph.

```
SKILL = {
  id      'mul-facts'          stable, never renamed — the profile keys off it
  name    'Times tables'       what a grown-up calls it
  strand  'number'             number | fractions | measure | data | algebra ...
  grade   3.0                  nominal grade, used for ordering and reporting
  needs   ['add-carry']        prerequisites: ids that must be mastered first
  gen(rand) -> ITEM            generates its own questions, endlessly
  why(item) -> [steps]         the worked solution, line by line, with reasons
  rule    'carry-tens'         which rule a miss here breaks
}
```

`needs` is what makes it a graph rather than a list. A learner does not walk a
straight line: they can be strong in number and weak in fractions, and the
graph lets both be true at once. **Nothing is ever gated on age or grade —
only on the prerequisite skills actually being mastered.**

Adding a subject = adding skills. The engine never changes.

## 3. ITEM CONTRACT

```
ITEM = {
  q       display HTML for the question
  plain   the same thing as plain text, so a checker can re-derive it
  ans     the exact answer (rational, kept exact — 0.75 and 3/4 are equal)
  kind    'num' (typed) | 'mc' (multiple choice) | 'pick'
  choices [{plain, correct, why}]   for 'mc' — every wrong one explains itself
  steps   [{line, why}]             the worked solution
  rule    the rule this item exercises
  traps   [{val, why}]              named wrong answers, each with its own
                                    explanation, so a sign error and an
                                    order-of-operations error get different words
}
```

**`plain` is not decoration.** It exists so an independent checker can re-derive
every answer from the question text alone, which is how SOLVE's 5,600 items
were verified. Any skill whose `plain` cannot be re-derived is a skill that
cannot be trusted.

**Prefer typed answers over multiple choice.** Four choices means a quarter of
wrong answers come back right, and that guess floor corrupts placement. Where
multiple choice is unavoidable, the promote gate has to be harder — see §5.

## 4. THE WHY ENGINE — the actual point

On a miss the learner never just sees the answer. In order:

1. **Name the rule.** Not "wrong" — *"you added before you multiplied; times
   beats plus outright."*
2. **If the specific wrong answer is recognised**, say what that slip was. A
   sign error and a place-value error deserve different sentences. That is what
   `traps` is for.
3. **Walk the solution one line at a time**, each line saying what was done and
   why, revealed on a tap so they read it rather than skim it.
4. **HINT gives the next step, never the answer.**
5. **Log the rule that broke**, and bring that rule back deliberately later.

There is no red, no buzzer and no "incorrect" anywhere. Missing something costs
progress toward a reward; it never takes anything away.

## 5. PLACEMENT AND PUSH

Same engine that measured out correctly in TALLY and SOLVE, and every rule in
`GAME-RULES.md` §12 applies here:

- Start at the floor of the graph and climb. **Never ask what level they are.**
- A skill is **mastered** at a sustained accuracy over enough attempts, not at
  one lucky streak.
- **Probe upward** into a skill whose prerequisites are met, and require the
  probe to confirm itself twice before it counts.
- **Mind the guess floor** — a harder promote gate wherever choices are few.
- **Demote fast** on repeated misses so they are never left drowning.
- **Review** old skills on a spaced schedule (Leitner boxes), weighted toward
  the rules they keep breaking.
- **Resume, never re-place.** The profile is the record of where they are.

## 6. THE RECORD — growth that outlives the browser

`localStorage` alone is not good enough for something tracked over years: clear
the browser or switch to the iPad and it is gone.

- **PROFILE** — per skill: attempts, correct, box, last seen, mastered-on date.
  Plus a dated history of mastery counts per strand, for the chart.
- **Interactive growth chart** — skills mastered over time per strand, hoverable
  and readable by a grown-up in five seconds. This is the thing the family
  actually wants to see.
- **EXPORT to CSV** — one button, the whole record, opens in Excel.
- **IMPORT** — so a profile moves between devices, and so a backup restores.
- Long term: the export belongs in the brain repo so a dead laptop costs
  nothing.

## 7. WHAT SHIPS FIRST

Engine + **one spine: maths, grade 3 to 6** + the why layer + the chart +
export/import. Maths first because it generates most cleanly and its ladder is
unambiguous, so the engine gets proven against the easiest case before reading
and writing are built on it.

Then: reading, then writing, then upward through the grades. Same engine, more
skills.

## 8. VERIFICATION — non-negotiable, same as every game here

- Every generated item re-derived by an **independent checker** that does not
  share code with the generator.
- Every worked solution checked to actually end at the stated answer.
- Every hint checked to not contain the answer.
- **Simulated learners of known ability** driven through the real engine, to
  confirm they settle where they should and stay in the 75-85% band.
- No failure language anywhere — asserted, not assumed.
- Phones first, both orientations, every tap target 40px+.
