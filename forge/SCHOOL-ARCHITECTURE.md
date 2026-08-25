# THE FORGE — architecture

**The Forge School** — "a school built to help kids forge their journey in life
and forge into the future." Named 2026-08-23. A logo is coming; when it does it
gets redrawn procedurally into a canvas like every other piece of art in this
arcade, because no game folder here carries an asset file.

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

## 3b. WHICH FIELDS ARE HTML AND WHICH ARE TEXT

Not written down until a pack author hit it, so it is written down now.

| field | treated as |
|---|---|
| `q` | **raw HTML** — may carry markup |
| `steps[].line` | **raw HTML** — may carry markup |
| `why`, `rule` | escaped text |
| `steps[].why` | escaped text |
| `choices[].why`, `ansText` | escaped text |
| trap explanations | escaped text |

So an entity like `&sup2;` written into a `why` renders on screen **as the
literal characters `&sup2;`**, not as a superscript two. Escaped fields take
plain text only. `q` and `steps[].line` are the two places markup belongs.

A useful side effect of keeping `steps[].line` in plain ASCII (`-` and `x`
rather than `&minus;` and `&times;`) is that an outside checker can then find
a negative answer like `-7` in the working. The audit checks exactly that.

Allowed tags in `q`: `span br b i sup sub table thead tbody tr td th div`. The
audit extracts every tag name and rejects anything else.

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
  the rules they keep breaking. For a long time this line was a promise the
  code did not keep — review picked uniformly among due skills and no rule was
  ever logged. It is real now, and asserted from the OUTCOME in forgeplay: a
  skill with a recent miss comes back in review about five times as often as
  one she sails through, the broken rule is tallied, and the tally DECAYS as
  she gets it right again — current trouble, not a permanent record. The
  record screen names the top three under "Worth another look together", and
  says nothing at all when there is nothing to say.
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

## 7. WHAT IS BUILT — as of 2026-08-24

**192 skills across 12 strands, grade 3 to 12 — every strand now reaches the top.** Maths went first because it
generates most cleanly and its ladder is unambiguous, so the engine was proven
against the easiest case before anything else was built on it. Then language,
then science, then reading.

| strand | skills | what it covers |
|---|---|---|
| number | 20 | carrying, times tables, place value, operations |
| fractions | 12 | equivalence, simplifying, all four operations, mixed numbers, fraction of an amount, decimals |
| measure | 11 | units, conversion, perimeter and area |
| data | 11 | tables, charts, averages, mean from a tally, two-way tables, probability up to at-least-once and expectation |
| algebra | 24 | expressions, equations, inequalities |
| words | 8 | plurals, pasts, comparatives, affixes |
| grammar | 13 | a/an by sound, agreement (plain and hidden-head), fewer/less, adjective vs adverb, pronoun case, double negatives, lie/lay, who/whom, fragments, run-ons, homophones |
| punctuation | 12 | end marks, commas in lists, commas of address, comma before and/but/so, apostrophes for one or several owners, semicolons, colons, commas round an added clause, dashes and brackets |
| word roots | 17 | prefixes, suffixes, Latin and Greek roots, word building, working out an unfamiliar word, in/im/il/ir, part of speech, disguised spellings, connotation |
| science | 24 | matter, materials, living things, fair tests, earth and space, forces, circuits, water cycle, photosynthesis |
| reading | 20 | literal recall, sequence, pronouns, cause, feeling, inference, vocabulary in context, main idea (stated and unstated), fact vs opinion, purpose, conclusion, comparison, evidence |
| writing | 15 | ordering, topic sentences, paragraph unity, transitions, pronoun clarity, tense consistency, parallelism, modifiers, redundancy, passive both ways, run-on repair, evidence, register, closings |

Run `.tools/forge-checks/forgecheck.js` for the live count per strand rather
than trusting a number written in a document.

Word roots was one skill and is now 17; punctuation was four and is now 12;
**writing landed 2026-08-24 with 15 skills**, the last subject. It was the
hardest to build honestly, because most of what a writing teacher marks cannot
be decided by rule and this file has no language model to judge prose — so
every skill is one where the answer follows from something checkable (a name
before its pronoun, a subject the opening phrase can grab, items sharing a
form), and everything that came down to taste was left out and is named in the
pack's own header comment. **Grammar and fractions were filled out the same
day — no strand is thin any more.** Grammar deliberately leaves out "was/were
after if" (the subjunctive is genuinely divided in modern use) and collective
nouns ("the team is/are", where British and American English disagree) — an
item with two defensible answers is a broken item.

**Reaching grade 12 is a property of the graph, not of a long list.** Skills
declare `needs`, so depth comes from prerequisite chains rather than from
hand-writing thousands of levels.

Then: reading, then writing, then upward through the grades. Same engine, more
skills.

## 7b. LAYOUT — two standards, on purpose

A maths or science question is **glanced at**. The numbers, the table and the
box the answer goes in have to be on screen together; if she has to scroll to
re-read the question after reading the table, she is holding data in her head
for no reason and the item is harder than the skill it claims to test. These
must fit with no scrolling on every device in the matrix.

A reading passage is **read**. Seven sentences plus four full-sentence options
do not fit in the ~250px a phone held sideways actually has, and the only way
to force it would be type too small to read — which is worse, and worst for the
child this was built for. Scrolling through a passage is what reading on a
phone is. For these the bar is that nothing is unreachable: no line above the
top edge, the box genuinely scrolls, and the options stay in view the whole time
so she can always see what she is choosing between.

The part that must never move is **the question**. Held sideways it was the
question that scrolled out of sight, leaving a child choosing between four
sentences with no idea what was asked. The passage scrolls inside its own box;
the question is pinned under it.

## 8. VERIFICATION — non-negotiable, same as every game here

- Every generated item re-derived by an **independent checker** that does not
  share code with the generator.
- Every worked solution checked to actually end at the stated answer.
- Every hint checked to not contain the answer.
- **Simulated learners of known ability** driven through the real engine, to
  confirm they settle where they should and stay in the 75-85% band.
- No failure language anywhere — asserted, not assumed.
- Phones first, both orientations, every tap target 40px+.

## 9. THE AUDITORS

Ten of them, in `.tools/forge-checks/`, each re-deriving what the game claims
with code that **shares nothing with the generator**. A generator checked by its
own logic only proves it is self-consistent. See that folder's README for what
each one proves; the short version:

`forgecheck` arithmetic, the skill graph, and the privacy promise ·
`langcheck` language rules re-derived from scratch ·
`readcheck` lookup-vs-inference, and that no tell reaches mastery ·
`scicheck` table soundness and every fact traced back to its table ·
`tablecheck` layout on three device profiles, both standards ·
`vocabcheck` word roots against their own tables, and that **no wrong option is ever also correct** ·
`writecheck` writing against its banks, re-checking each RULE from the raw text rather than the pack's labels ·
`forgeplay` simulated learners through the real engine, the why layer, the record ·
`hubcheck` that the arcade hub card and the game agree ·
`charttest` that the growth chart responds to pointer, finger and arrow keys about the same save

**The number the hub shows is written by the game, not re-derived by the card.**
The card once reported 85 skills solid where the game said 82, because the real
gate raises the bar on multiple-choice skills for the guess floor and the card's
copy of the rule did not know that. Telling a parent a child is further along
than she is, is the one direction this number must never be wrong in.
