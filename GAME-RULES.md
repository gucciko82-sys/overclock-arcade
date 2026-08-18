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
