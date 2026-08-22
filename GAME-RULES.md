# OVERCLOCK GAME RULES — how we build fast and don't break

Distilled from building and shipping 22 games. Follow these and a new game
goes from idea to live-and-verified in one sitting. Every rule here was
paid for — the trap it prevents is noted where it isn't obvious.

---

## 1. THE NON-NEGOTIABLES

1. **One folder, one `index.html`, zero dependencies, zero asset files.**
   All art drawn procedurally into canvas at load, all sound synthesized
   with WebAudio oscillators. A game folder copied anywhere still works.
2. **Phones first, BOTH orientations.** Every game must be playable on an
   iPhone held either way. Decide the strategy up front:
   - *rotate the board* (Overflow, Airlock — simulate in one space, rotate
     only render + pointer math), or
   - *letterbox a fixed-aspect stage* (Tilt, Kilobyte, Ember), or
   - *fluid full-screen world* (Overdrive, Airtime, shooters).
3. **Three input paths, always: keyboard, touch, gamepad.** Touch appears
   only after a real touch (`body.touch` class), never by sniffing — and
   touch UI must ALSO be gated behind `body.playing`, or the buttons lurk
   under the title menu (Voidrunner shipped that bug).
4. **Nothing ships until scripted play has beaten it.** Not "it loads" —
   the core loop, the win path, the lose path, and the weird path
   (multiball, FINISH THEM, fare bail) each verified by driving the game
   from Playwright and asserting on state. Reading the code is not
   verification; three of our best bugs were invisible in source.

## 2. THE SKELETON (copy from any recent game)

- CSS custom-property tokens: `--bg #0b0f1e`, `--accent #ffcc4d`, `--fg`,
  `--dim`, `--panel`, `--line`. Segoe UI stack. Gold titles with glow.
- DOM: `#stage > canvas#game` + `#topbtns` (44px icon buttons, top-right,
  hidden unless `body.playing`) + optional touch controls + `#overlay`
  holding `.card` menus.
- Overlay cards: eyebrow → h1/h2 → tagline → `.keys` help grid → stats →
  buttons with `data-act`, one delegated click handler. **Cards must fit a
  342px-tall viewport** (that's the REAL usable height on an iPhone in
  landscape — not 390): `@media (max-height: 620px)` hides `.keys`, and
  `#overlay { overflow-y: auto }` as the backstop so no button can ever be
  unreachable.
- Boot order: build state → `resize()` + ResizeObserver on `#stage` →
  `setMuted(loadStr(...))` → `titleScreen()` → `requestAnimationFrame(frame)`.

## 3. THE LOOP

- RAF-driven. Clamp dt: `raw > 0.05 → 0.05`, `< 0 → 0`. A stall must never
  teleport anything.
- **Auto-pause on `blur` AND `visibilitychange`.** Games freeze when their
  tab stops compositing; without auto-pause that reads as a hang, and with
  hidden-window testing it reads as a broken game (cost us an hour on
  Starfall). Corollary: playtest headless, or keep the window fronted.
- Fast movers get fixed substeps (pinball: 5, air hockey: 4). Cap speeds.
  Axis-separated wall collision so things slide instead of sticking.
- No `Date.now()` / wall-clock in game logic — dt accumulation only.

## 4. LAYOUT LAW

- **Top-right 100×52px belongs to the icon buttons.** Canvas HUD never
  draws there. Score top-left, big clock top-center, game-specific right
  edge BELOW 52px.
- **Every tappable thing ≥ 40px** in both dimensions, at every width —
  check the narrow-screen media queries too (Firewall's buttons were fine
  at 44px until the row clipped at 390px wide; the fix is a width media
  step-down to 40px, not letting it clip).
- Touch buttons: bottom corners, `env(safe-area-inset-*)` margins, one
  side movement / other side actions.
- No DOM element may overlap another interactive element. `ui-audit.js`
  checks all of this by machine — run it, don't eyeball it.

## 5. AUDIO

- One lazy `AudioContext`, created on first gesture (`initAudio()` in
  every input handler — iOS requires it), master gain, `setMuted`
  persisted to `<game>_muted_v1`.
- SFX = short envelope-shaped oscillator sweeps; percussive = filtered
  noise bursts. Continuous sounds (engines) = one persistent oscillator
  whose frequency/gain track state — never per-frame spawning.
- Every sound cue also has a visual cue. Muted play must lose nothing.

## 6. STATE & SAVES

- `localStorage` key `<game>_v1`, JSON, written on game over / new best
  only. **Defensive reads everywhere** — the hub peeks into every game's
  save and a corrupt value must render as "Unplayed," never crash.
- The hub card's `best()` reader and cover painter go in the hub's GAMES
  array the same commit the game ships.

## 7. FEEL (the difference between "works" and "good")

- Input buffering: queued turns (Overflow: 3 deep), buffered direction at
  tile centres (Kilobyte), held-key state objects — never raw keydown in
  the sim.
- Assists that remove fake difficulty: door funneling (Kilobyte), ball
  saver (Tilt), coyote time (Ember). If the scripted bot keeps failing at
  something a human "should" manage, the geometry is wrong, not the bot.
- Juice checklist: screen shake (capped, decaying), hit-stop or slow-mo on
  big moments, floaters for every score event, particles on every impact,
  banner cards for phase changes. Cascading multipliers make everything
  more fun (Defrag chains, Airtime combos, Overdrive ratings).
- Difficulty ramps with progress, never all at once: per-level speed
  (Overflow), per-wave counts (Downlink), per-round AI (Deadlock).

## 8. VERIFY & SHIP (the pipeline, in order)

1. `node dev-server.js 3020`, build the game.
2. **Syntax gate**: `new Function(scriptText)` — catches breakage before
   any browser time.
3. **Scripted play**: drive the real game; assert score changes, state
   transitions, death, win. Cheat freely (teleport, set hp) — the point is
   exercising paths, not honesty.
4. Register in `playtest.js` (exact-match quoted selectors — `text=X` is a
   SUBSTRING match and will click help text; `text="X"` is exact) and in
   `ui-audit.js` START map. Turn-based games get `staticOk: true`.
5. Run the 3-profile matrix (Chromium desktop + WebKit iPhone both
   orientations) and `ui-audit.js`. Zero console errors, zero overflow,
   all controls legal. WebKit-headless RAF of 10–25/s is normal; only
   near-zero means frozen. Voidrunner (WebGL) can't run headless — front a
   real browser for it.
6. **Eyeball the play screenshots.** Geometry checks can't see canvas art;
   screenshots caught the flung rooftops, the wall stubs, the buried dog.
7. Hub card (procedural cover, no images) + README table row + dated
   README log entry in the house voice — including what was found and
   fixed, so the next builder doesn't relearn it.
8. Commit family-programs (hooks run the responsive matrix), push, sync
   the deploy mirror (`overclock-mirror`: copy folders + hub + README,
   re-apply the relative-icon-path sed), push, verify the live URL with an
   `until curl | grep` loop. **curl to the Vercel URL hits a bot wall —
   verify the GitHub Pages mirror or use a real browser.**

## 9. NAMING & THEME

House names are one punchy word from computing, ideally a pun on the
mechanic: Overflow (snake = growing buffer), Deadlock (fighting processes),
Airlock (air hockey), Defrag (match-3), Downlink, Kilobyte, Tilt. The
fiction is "inside the machine": daemons, packets, sectors, processes.
Score currencies: bits, credits, cash. Death screens get themed headlines
(KERNEL PANIC, BUFFER OVERFLOW, DISK FULL, FARM DOWN).

## 10. DON'T RELEARN THESE

- A game that "does nothing" in a hidden window is paused, not broken.
- Playwright's unquoted text selector clicked "Mouse (vs CPU)" instead of
  the VS CPU button. Quote for exact match.
- WebKit landscape iPhone: usable innerHeight ≈ 342px, not 390.
- Multiplying a parallax offset by its scale factor twice flings art off
  the screen only at the edges — screenshot the CENTER AND the edges.
- Adding `padding` to compress a card ADDS height if the card had none.
- Off-board tiles can count as walls for physics while never drawing
  wall segments (Kilobyte's edge stubs).
- Match-3 boards must be generated with no matches AND at least one legal
  move; reshuffle preserving the multiset when moves run out.
- An endgame the bot can't reach isn't tested (Firewall's unwinnable boss
  and Deadlock's re-triggering FINISH THEM were both endgame-only bugs).

---

## 11. BUILDING SEVERAL GAMES AT ONCE

Parallel builds work — one game per folder is a clean split, since the only
shared files are the hub, the README and the two harness files. Rules that
made it work, and one that had to be learned:

- **The builder writes ONLY `29_games/<id>/index.html`.** The hub card,
  README row, `playtest.js` and `ui-audit.js` registrations are the
  integrator's job. Two builders editing the hub array is a merge fight.
- **Give every builder its own scratchpad subfolder.** Three builders
  sharing one scratch directory silently overwrote each other's
  `syntax.js` / `play.js`, and one syntax gate validated a *different
  game's* file and passed. A green check on the wrong file is worse than
  a red one. `scratchpad/<game>test/` per builder.
- **The integrator re-verifies every game itself** — syntax gate, the
  3-profile matrix, `ui-audit.js`, and its own look at the screenshots.
  A builder's report is a claim, not evidence; the point of the second
  pass is that it cannot inherit the first pass's mistakes.

---

## 12. ADAPTIVE LEARNING GAMES — the ladder rules

Every learning game here places the learner by playing with her rather than
asking her. Char, Echo, Tally and the rest all use the same engine, and every
rule below was paid for by a game that passed its own tests while placing a
learner wrong.

- **Never ask for a difficulty. Never design against an age or a grade.**
  Start at the floor, climb on success, and let the ladder find her. Age tells
  you nothing about the rung — a child can be eleven and working several years
  below, and be nowhere near the same rung in two different subjects.
- **Low floor, high ceiling.** The bottom rung must be gettable by someone who
  is genuinely struggling; the top must be real work. A game she can exhaust
  has told her she is finished.
- **Promote on a run, demote fast, clear the recent window on any move.**
  Demoting fast protects confidence; clearing the window is the hysteresis that
  stops it yo-yoing.
- **A probe must confirm itself.** Ask one rung up periodically, and require
  TWO consecutive correct probes before promoting. One lucky tap must never
  hand her a level. (Char and Echo both shipped promoting on one.)
- **MIND THE GUESS FLOOR — this is the one that keeps getting missed.** Two
  choices means half of all wrong answers come back right; three means a third.
  So "N in a row" is not the same evidence at every rung. Most activities widen
  from two buttons to four as they climb, so the floor falls from 50% to 25%
  and quietly brakes the climb — but any activity that *cannot* widen (Tally's
  WHICH HAS MORE: comparing five piles at once is a worse question) sits at a
  50% floor the whole way up, and a flat gate drifts a floor-level learner a
  full rung above her true ability on luck alone. **Make the gate harder where
  the guess floor is higher** — one more in a row, one more confirming probe.
  Prefer typed or constructed answers wherever the content allows; they have no
  guess floor at all.
- **RESUME the found rung between sessions.** Re-testing her every time is its
  own small insult.
- **Teach on a miss, do not just reveal.** Name the rule, then walk the answer
  out step by step saying what is being done and why. A HINT gives the next
  step, not the answer.
- **Zero failure language.** No red, no buzzer, no shake, no "wrong", no
  "incorrect", no "try again". Assert this in the tests — grep the generated
  scripts for it — because it creeps back in.
- **Show growth to the grown-ups**: rung per skill, moved over time.

### How to actually verify a ladder

Tests that ask "does promote() promote?" pass on a broken ladder. The only
thing that finds the real bug is to **simulate a learner of known ability and
see where the ladder settles**:

- Model ability as a **SMOOTH curve, not a cliff**. A sharp cliff (95% at her
  rung, 67% one above) puts the 75-85% target band *between* rungs, where
  nothing can ever land, and makes a healthy game look unfixable. That has cost
  a session already.
- **Model the learner you mean.** Centre the curve so "ability = rung N" means
  she is genuinely competent at N (~85%), not half-mastered (~50%). Getting
  that wrong makes a healthy ladder read as far too harsh — it happened again
  on Tally and cost a round of pointless tuning.
- Model the **guess floor** explicitly from the number of choices each rung
  shows.
- Run several abilities x several seeds. Report **settled level vs true
  ability**, **accuracy at level** (want 75-85%), and **level moves per 100
  items**. Settling more than about a rung from true ability is a bug.
- Tune against that rig, and be willing to revert: a slower demote was tried on
  both Char and Tally and measured **worse** both times.

## 13. MORE THINGS NOT TO RELEARN

- **An `<svg>` with `width: 100%` and a viewBox computes its own HEIGHT from
  the viewBox ratio.** A 730px-wide card silently became 245px tall and shoved
  an unshrinkable button on top of it. Height has to be handed DOWN by the
  layout: let the row take the leftover space, the card fill the row, and give
  the svg `height: 0; flex: 1 1 auto` so the flex algorithm decides and the art
  letterboxes inside it.
- **Art that scales to fill its own container can answer the question for
  you.** In Tally's WHICH HAS MORE, each pile stretched to fill its own card,
  so a pile of two drew things twice the size of a pile of five — and "which
  has more?" gained a second, wrong answer: whichever things look bigger.
  Anything being *compared* must be drawn to a common scale.
- **Check that the position you are measuring is one the game can reach.** A
  first pass at Dunk's difficulty curve sampled a shooting spot 7.2 m out and
  reported that 97% of the release meter scored — `SPOT_MAX` is 6.60, so that
  was a spot no player can ever stand on. On legal spots the curve was a clean
  38% at the deepest to 75% point blank.
- **`parseBoard`-style text position parsers usually skip blank lines**, so a
  row of eight spaces collapses the board and shifts every square. Use dots for
  empty squares. Three apparent rule failures in Checksum's integration were
  entirely this — the game was right and the test was reading a different
  position than it had written.
- **Check the field names on a test hook before believing a failure.** Two
  "failures" today were assertions reading `G.perfect` where the game exposes
  `G.perf`, and `r.boardHits` where the probe returns `r.board`.
- **The hub peeks into every game's private save format, so its readers drift
  silently.** Char's card read a `.ok` field Char has never written, so it said
  "Unplayed" no matter how much she played — and nothing failed, because a
  reader that returns nothing looks exactly like a game nobody has played. Play
  each game for real, then read its card back off the hub; same origin, so
  localStorage survives the navigation.
- **Reconcile registrations against disk, not against the running tally.**
  Greedy shipped without being registered in either harness file and was
  silently skipped by every matrix run for days. `comm` the sorted folder list
  against the hub ids and both harness maps.
- **For a rules game, write a second implementation.** Checksum's draughts
  generator was compared move-for-move against an independently written one
  over 934 positions from fourteen seeded games — and the positions were then
  checked to actually contain the interesting cases (233 forced captures, 43
  multi-jumps, 17 crown-ends-chain, 559 backward king moves), because agreement
  on quiet shuffling proves nothing. For chess the equivalent is **perft**, and
  it is not optional.
- **WebKit no longer launches on the Windows machine.** Smart App Control
  blocks Playwright's `WebKit2.dll` ("An Application Control policy has blocked
  this file", exit `0xC0000142`). Do not turn Smart App Control off — it is a
  one-way change. The harness falls back to Chromium in iPhone emulation and
  says so; layout, overflow, tap-target and console findings still hold, and
  **real Safari behaviour now belongs to the iOS Simulator on the Mac.**
