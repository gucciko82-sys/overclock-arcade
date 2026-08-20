# 29_games — OVERCLOCK

Games built in-house. Each game is a folder with a single self-contained
`index.html` — no build step, no dependencies, no external assets. All artwork is
drawn procedurally into canvases at load time, so a game folder can be copied
anywhere and it still works.

Live at <https://overclock-arcade.vercel.app> (Vercel project
`o-connor-family/overclock-arcade`, public — SSO protection deliberately off, so
a 401 there is a regression).

Named by Michael, 2026-08-16. Note for later: "Overclock" is already used by
OverClock Studios and by an Arc Studios Roblox game — harmless for a personal
arcade, but it would need a differentiator before anything commercial. The older
`oconnor-arcade` project still exists and still serves the old build; delete it
from the Vercel dashboard whenever.

## Games

| Folder | Game | Notes |
|---|---|---|
| `voidrunner/` | **Voidrunner** | **The only true-3D game here.** Raw WebGL2, no libraries. Third-person flight through a procedurally streamed neon canyon that curves in all three axes. Rings, pylons, rotating gates, pursuit interceptors, graze multiplier. |
| `apex_run/` | **Apex Run** | Pseudo-3D arcade racer. Three circuits, seven rivals over three laps, a points championship, and 60 slower traffic cars to pick your way through. |
| `starfall/` | **Starfall** | Twin-stick neon vector shooter. Five enemy types (drifter, chaser, weaver, turret, Warden boss), escalating waves, weapon drops and screen-clearing bombs. |
| `neon_breaker/` | **Neon Breaker** | Brick breaker. Fourteen levels, armoured and explosive bricks, five power-ups (wide, multi-ball, sticky, laser, slow), combo multiplier. |
| `gridlock/` | **Gridlock** | Falling-block puzzle with the modern feel: hold piece, three-deep next preview, ghost piece, wall kicks, seven-bag randomiser, back-to-back and combo scoring. |
| `deep_run/` | **Deep Run** | Side-scrolling cave flyer. Thrust physics with real momentum, procedural caves, mines and pursuit drones, and a near-miss multiplier for flying close to the rock. |
| `gravity_grip/` | **Gravity Grip** | Two-wheeled physics rider. Wheel bodies and a chassis joined by spring-damper sliders, fixed 1/240 s solver. Procedural terrain with kickers, tabletops, whoops and gaps; air pitch control, fuel cans, coin arcs. |
| `firewall/` | **Firewall** | Tower defence on a circuit board. Three maps, five towers each with three tiers and a two-way specialisation, six intrusion types, shielded ROOTKIT bosses on waves 5/10/15/20, then endless. |
| `flyway/` | **Flyway** | Light-gun duck shoot, Duck Hunt by way of a neon marsh at dusk. Five shells a flush, ten birds a round, an escalating quota, and a retriever who surfaces holding your birds or laughing in your face. |
| `ember/` | **Ember** | Precision platformer. Twenty-two levels of run/jump/dash with coyote time, tuned so every death reads as fair. Touch pad on phones. |
| `null_sector/` | **Null Sector** | Real-time action roguelike. Six procedurally generated floors, a boss on each, shops, treasure rooms, and 28 stacking passive upgrades plus 6 active items. |
| `kilobyte/` | **Kilobyte** | Maze chase on a motherboard. 152 bits a board, four ROOT ACCESS nodes, and four daemons running four different target brains (chase / ambush / flank / coward), scatter-chase mode clock, payload bonuses, tunnel wrap. |
| `downlink/` | **Downlink** | Missile defence. Three uplink batteries (centre shoots faster), six server nodes, MIRV splits, bloom-dodging smart bombs from wave 6, a warhead-dropping drone from wave 3, wave tally for unused interceptors and surviving nodes, a banked spare node every 10,000. |
| `overflow/` | **Overflow** | Snake. 23x15 board that rotates to stay big on portrait phones, speed tiers every 8 packets, timed bonus glitch, buffered turns (up to 3 queued, reverses rejected), swipe steering. |
| `deadlock/` | **Deadlock** | One-on-one fighter, and the arcade's first 2-player game (shared keyboard). SYN vs ACK, best of three, hold-away blocking with chip damage, meter specials (PING projectile / SLAM dash uppercut), knockdowns, CPU with a per-round difficulty ramp — and a FINISH THEM sequence where landing the last hit throws a FATAL EXCEPTION and derezzes the loser. |
| `airlock/` | **Airlock** | Air hockey, first to seven. True multitouch 2-player — each player drags their own mallet on one phone/tablet — or WASD vs arrows, mouse or gamepad vs the CPU. Table stands upright on portrait screens and lies sideways on desktops; substepped physics so the puck never tunnels; CPU that intercepts, strikes around pinned pucks, and ramps with your streak. |
| `defrag/` | **Defrag** | Match-3. 8x8 board, six sector shapes (shape + colour, so colourblind players can play), cascade multipliers, match-4 scanline bolts, match-5 colour purges, quota-per-level with move budget, idle hints, auto-reshuffle when no moves exist. |
| `airtime/` | **Airtime** | Trick motocross — the jumps game (Gravity Grip stays the survival ride). Three built courses of kickers, tabletops, doubles and step-ups; real rotation physics with flip counting, landing-angle judgement (clean / sloppy / WRECKED), combo multiplier, checkpoints, time bonus, pulse-wave two-stroke engine. |
| `tilt/` | **Tilt** | Pinball, three tables: BOOT SECTOR (bumper triangle, left target bank), HEATSINK (bumper diamond, V-baffle fins, right bank), MOTHERLODE (crown bumper, centre island vault, horizontal bank). Segment physics at five substeps, flippers that impart real rotational velocity, slingshots, ball saver, drop-target multiball per table, TILT/HEAT/RAM rollover letters for bonus multipliers, and a three-nudge tilt that kills the flippers. Per-table high scores. |
| `solitaire/` | **Solitaire** | Klondike on neon felt, procedurally drawn cards. Draw-1 or draw-3, tap-to-auto-move or full drag-and-drop (multi-card stacks), unlimited undo via state snapshots, flip scoring, an AUTO button that plays the endgame once everything is face up, and a bouncing-card win cascade. |
| `overdrive/` | **Overdrive** | Crazy Taxi-style open city, built for Amber. Procedural 8x8-block neon city with 2.5D parallax rooftops and lit windows, drift handbrake physics with skid marks, traffic, riders who wave from the curb, timed fares with CRAZY/GREAT/OK ratings and tips, clock extensions per delivery, oscillator engine that pitches with speed. |
| `quadcore/` | **Quadcore** | Top-down night-trail ATV racing. Three seeded forest loops (HOLLOW / MUDLINE / SWITCHBACK), three laps against three rubber-banded rivals, mud that eats momentum, wooden ramps, nitro cans, coins, tree collisions, headlight cones and fireflies. Per-track record times. |
| `prom/` | **Prom** | The princess game (and the barbie game) — Princess of the ROM kingdom. A dress-up studio (5 skin tones, 4 hairstyles x 8 colours, 4 crowns, 4 gown silhouettes x 10 colours, sparkles, shoes, extras) and a royal-ball finale with a waltz, a spotlight walk, twirls, fireworks and an adoring court. No timers, no losing. Counts royal debuts. |
| `scope/` | **Scope** | The hunting game, and the arcade's first fully naturalistic one — no neon, just first light. Deer (does and 4-to-10-point bucks) and turkey (hens and strutting toms) drift into a misty dawn meadow; five tags, a 2.5-hour morning compressed into 150 seconds, a magnified scope lens rendered by drawing the whole scene twice, and breath you hold to steady the sway. Calm animals score double — wait for the feed. Miss and the whole field bolts. Saves best morning and best buck. |
| `cast/` | **Cast** | The fishing game — you cast a line, code casts a type. One evening on a golden-hour pond, naturalistic like Scope: bluegill, crappie, largemouth bass and channel cats, each holding its own depth band, each with real weight ranges and its own fight. One button does everything — hold to charge the cast, tap to set the hook when the bobber dips, hold to reel and let go before the tension bar snaps the line. Bass jump, cats bulldog, the pond occasionally hands you a boot. Saves best evening (total pounds) and best fish. |
| `smash/` | **Smash** | Monster truck freestyle ("smashing the stack" is a real term; so is smashing a minivan). Seventy-five seconds under the floodlights: two-wheel-plus-chassis physics with real suspension, eleven junk cars and a bus that crush flat in three stages each, three dirt ramps, backflip/frontflip detection off cumulative air rotation, airtime points, a combo multiplier up to x5, and a crowd that bobs harder the hotter your chain gets. Three rollovers and the show is over. |
| `chip/` | **Chip** | Mini golf (a silicon chip; a chip shot). Nine holes, par 28: doglegs, bunkers, twin ponds with a causeway, stone bumpers, offset gates, an island green, and TAPEOUT which combines the lot. Hold to charge a ping-pong meter, release to strike; adaptive-substepped physics so the ball never tunnels a rail, sand at 4.2x friction, and a cup that lips out if you arrive too hot. Scorecard with birdies and bogeys; best round saves. Board rotates 90 degrees in landscape so the whole hole fills a phone held either way. |
| `patch/` | **Patch** | A garden patch; a software patch. Twelve plots of warm dirt and five crops — carrot, tomato, sunflower, corn, pumpkin — each drawn distinctly through five growth stages. One tap does whatever the plot needs next: till, plant, water, harvest. Baskets sell for coins, coins buy seeds, earnings unlock the pricier ones. A sun arcs through the day, rain showers water the whole patch for free, and bees and butterflies shelter when it rains. No timer, no enemies, nothing dies — thirsty plants simply wait. The garden is saved and still there when you come back. |
| `pitch/` | **Pitch** | Home run derby (you pitch a ball; you pitch an idea). Side-on ballpark at golden hour: the pitcher winds up and throws one of four pitches that genuinely fly differently — fastball 0.64s at 97 mph, slider, changeup off the same arm slot, and a curve that humps and falls at 0.96s and 79 mph. One button, timed against a 155ms contact window; W/S sets the swing plane. Real drag and backspin Magnus lift, so a barrel leaves at ~102 mph and 33 degrees and carries about 400 feet. Ten outs ends the round; the camera follows the ball out and reveals the 375-foot wall so you can see what it has to beat. |
| `spare/` | **Spare** | A spare part; a bowling spare. Ten frames down a honey-maple lane with 39 drawn boards, the arrows in their staggered V, and recessed gutters. One button locks stance, then power, then hook; an oil pattern keeps the lane slick to 20 ft and dry past 44, so the hook bites late. Ten colliding pin bodies where a toppling pin sweeps its neighbours — which is where strike carry actually comes from. Real ten-pin scoring: a perfect game is exactly 300. |
| `grind/` | **Grind** | Grinding a CPU; grinding a rail. A concrete park at dusk — quarter pipes, a funbox, flat bar, stair set with handrail, ledge and bowl. Ollie, kickflip, heelflip, shove-it, 180 through 720 spins, five grind types, and manuals on an unstable balance meter. Everything chains into one line while you stay off the ground, banked on a clean landing and lost entirely on a bail. 90 seconds a run. |
| `cache/` | **Cache** | Cache memory; a memory game. Concentration with twelve procedurally drawn symbols — chip, resistor, capacitor, diode, cell, trace, gear, bolt, magnet, key, star, moon — all distinguishable by shape so colour is never load-bearing. Three board sizes, cards that genuinely turn over on their axis, a chain bonus for consecutive matches, and best-per-size records. No fail state. |
| `parse/` | **Parse** | Parsing a string; puzzling out a word. Five letters, six guesses, 402 hand-reviewed family-safe answers against a 1,062-word accepted list. The duplicate-letter rule is the two-pass one done properly — guess EERIE against CRANE and exactly one E is marked. Colourblind-safe by shape as well as colour: exact tiles carry a corner wedge, present tiles a dashed border and a dot. Streak, best streak and a guess-distribution chart. |
| `botnet/` | **Botnet** | Fixed shooter, Galaga school. Squads swoop in on bezier entry paths, settle into a formation that breathes and sways as one organism, then peel off in dive runs that fire aimed shots — divers are worth double. Four bot types (drone/worm/brute/harvester), kill-chain bonus, SPAM envelope bonus ship, accuracy bonus per wave, slow-mo on harvester kills, extra life every 15,000 bits. Drag-to-fly with autofire on phones. |

### Built and play-tested 2026-08-17 — Flyway

New game, built to request: "a game like Duck Hunt." Ducks flush from the
reeds, arc across a dusk sky, and bolt for the top if you are slow. Five
shells per flush, ten birds per round, quota climbs from 6 toward 9, flushes
grow from one bird to three. The dog works the reed line, leaps in, and comes
up either holding your birds or laughing at you.

Aiming is a real pointer — mouse position, the tap point, or a stick-driven
reticle — and firing is instant hit-scan, which is what makes a light-gun game
feel honest. Everything is drawn procedurally: sky, moon, hills, treeline,
cattails, dog and birds. Audio is oscillators only, so the shotgun is a stack
of detuned saws collapsing in pitch with a bright crack on the front rather
than a noise buffer.

Found and fixed by playing it, not by reading it:

- **`beginRound()` never hid the overlay.** Clicking NEXT ROUND left the
  round-clear card sitting on screen with the birds already flying behind it.
  Only `startGame()` hid it.
- **The scene was clipped to ~76% of the canvas.** `resize()` runs before the
  layout settles, so the first frame was drawn at stale dimensions. Verified by
  scanning the backing bitmap for painted pixels: 0.768 of the width before,
  0.999 after. The loop now re-checks the stage size each frame, which also
  covers orientation changes and mobile browser chrome.
- **PAUSE sat on top of the bagged tally on a phone.** The touch bar is pinned
  to the bottom and the HUD bottom row was too — exactly the DOM-over-DOM
  collision that only appears at phone widths. The HUD now reserves space.
- **Hills buried the warm horizon band**, and the moon reflection was a
  linear-gradient `fillRect` that kept its hard left and right edges and read
  as a grey box on the water. Hills dropped to just above the treeline;
  reflection is now radial and clipped to the marsh.
- **The dog was a gold scribble.** Glowing wire outlines do not read as an
  animal against a dark marsh. He is now a filled silhouette — coat, cream bib
  and muzzle, floppy ears — with the neon kept to a thin rim, and he draws in
  *front* of the reeds when he surfaces. His pose also holds 2.6s instead of
  1.4s, because the laugh was over before it registered.

- **The dog was rebuilt.** The first pass was primitive shapes in glowing wire
  outline, which read as a scribble rather than an animal. He is now drawn with
  volume: gradient coat so the chest and skull look round, scalloped fur along
  every free silhouette edge, floppy ears with inner-ear colour, a cream blaze
  and muzzle, a nose with a highlight, whiskers, brows, and a moon-side rim
  light picked up from the sky behind him. Laughing he screws his eyes shut and
  shows teeth and tongue; retrieving he carries the birds in his jaws. Held
  birds now draw last -- behind the head they were hidden by the skull, which
  rather defeated the point of retrieving them.
- **Shells raised from three to five per flush.**

Verified: hit detection lands 10/10 with a scripted gunner, both end states
fire correctly ("PERFECT ROUND" card advances and clears; missing the quota
gives "THEY GOT AWAY"), and the laughing dog renders — confirmed by sampling
canvas pixels in his box rather than by racing a screenshot.

### Verified 2026-08-17 (later) — Firewall

Play-tested by scripting a commander that builds, upgrades and runs waves, then
reading the boss's hit points frame by frame. It found a fault of exactly the
same class as Neon Breaker's sealed level: the game could not be won, and the
source read fine.

- **The wave-5 ROOTKIT was invulnerable.** Measured over 20 seconds of game
  time its HP never moved -- 1988, not a single point -- while its shield went
  568 -> 540 -> 568, fully regenerating. Shields regenerate at
  `sregen * hpScale(wave) * 0.35` = about 17/s at wave 5, which beats the total
  shield damage a wave-5 economy can field, and regen restored to **full**, so
  any progress was erased. The boss then always cashed in its 10-point leak,
  taking half of the player's 20 integrity, every game, on every map. Two boss
  leaks is death, so the run was effectively over before wave 10.
- **Fix, part one: a shield that has been fully broken stays broken.** Regen
  now only punishes letting up *before* you break through, which is the
  readable version of the rule and makes bosses a burst-damage problem rather
  than an unwinnable damage race.
- **Fix, part two: the boss was sized past what wave 5 can answer.** A wave-5
  defence puts roughly 700-1200 damage into it across its whole walk, against
  2556 effective HP. ROOTKIT is now 900 HP / 250 shield (from 1400/400) and
  leaks 5 instead of 10, so a good wave-5 defence kills it and a sloppy one
  pays a quarter of its integrity instead of half. `hpScale()` still scales
  bosses hard into the late waves.

Result: the same scripted commander now clears **all 20 waves of TRACE** --
"NETWORK SECURE", 448 packets destroyed, 1 leaked, 15/20 integrity -- where it
previously died on wave 10 every time. SPIRAL and CROSSBAR both build, place
and run correctly. The damage formula has a 12% floor, so no enemy is ever
literally unkillable and a wave can never hang.

### Verified 2026-08-17 (later) — Gravity Grip

Play-tested by driving the real game in a browser through a scripted rider, not
by reading the source. The reported symptom was "stalls at 440m". It was three
separate faults, and the distance was a red herring — nothing happens at 440m.

- **The run never ended, so the game looked frozen.** The out-of-fuel death
  check watched instantaneous speed: `if (sp < 0.7) deadTimer += dt; else
  deadTimer = 0;`. A bike parked on a hill still jitters on its suspension, and
  a *single* frame above 0.7 m/s reset the timer. Measured a bike stranded for
  2,442 consecutive frames — about 40 seconds — with an empty tank and the run
  still marked `play`. The only way out was a page reload. That is the "stall".
  Now measured against `dist`, which is monotonic and cannot be faked by jitter.
- **The bike could not climb the steepest ground the generator was allowed to
  build.** `MAX_RISE` was 0.90 (42 degrees), which needs
  `76 kg * 20 m/s^2 * sin(atan(0.90)) = 1017 N`, but the drivetrain delivered
  only `MAX_TORQUE / WHEEL_R = 300 / 0.36 = 833 N`. The slope clamp was
  advertised in a comment as the completability guarantee and did not hold.
  Worse, the Catmull-Rom surface *overshoots* that clamp at the kinks the clamp
  itself creates — measured a real slope of **1.17** against a 0.90 cap. Now
  `MAX_RISE = 0.60` against `MAX_TORQUE = 340` (944 N available, 782 N needed),
  which keeps even the overshoot peaks inside the torque budget. Downhills are
  not clamped, so the drops, kickers and big air are untouched.
- **The first fuel can was out of range.** A full tank is 100 units burning at
  `1 + 3` per second — about 25 seconds of throttle — but the first can sat at
  +130 m. A rider who bogged down even slightly ran dry before reaching one, and
  then bogged harder. First can moved to +92 m, spacing tightened to 88-124 m.

Result: runs that used to strand between 440 m and 741 m now go past **2,000 m**
under the same scripted rider, with fuel cycling healthily between 63 and 95.

Two guards were added after the first fix broke something else: the stranded
timer no longer counts while airborne, and it does not start until the run is
actually under way, because a fresh run that had not moved yet was being killed
at 0 m with "STUCK" seven seconds in.

### Verified 2026-08-17

All four new games load clean with no console errors, render correctly, and
respond to real keyboard input. Verified in-browser, not by reading code.

**Fixed after play-testing:**

- **Neon Breaker — level 14 `OVERCLOCK` was genuinely unwinnable.** Its barrier
  rows read `.5########5.`, sealing 30 breakable bricks inside a box whose only
  openings were the outer gutters. Those bricks still counted toward
  `bricksLeft`, and the ball's angle is capped away from horizontal, so it could
  never fly sideways into the slot. Barriers are now `.5###..###5.`, giving a
  two-column vertical channel. `OVERDRIVE`'s solid `############` row is fine by
  contrast — it is the top row, and walls are excluded from `bricksLeft`.
- **Starfall — title screen was clipped at both ends.** The overlay used
  `align-items: center`, so a card taller than the viewport (647px in a 627px
  window) split its overflow above and below and scrolled the header off-screen.
  Now `align-items: safe center` plus a short-screen media query. Card top went
  from −10px to +18px.
- **Gridlock — tap targets.** `SOUND ON` / `PAUSE` computed to ~27px and failed
  the 40px floor at every device size. Now `min-height: 40px`.

**Checked and found already correct:**

- **Deep Run's difficulty curve.** The agent's own note said the gap was pinned
  at the `SAFE_GAP` clamp, but it fixed that before finishing: breathing is now
  proportional (±13.5%) rather than a fixed ±39 units. Gap runs 300 → 132 with a
  low of ~114 against a clamp of 90, so it never touches the clamp.
- **Gridlock's scoring.** Hard drops award `dist × 2` and soft drops `+1`; an
  earlier note here claiming otherwise was wrong. The zero score seen in testing
  was pieces landing by gravity between tool calls, not a scoring bug.

**Still unverified:**

- **Gridlock line clears have never been observed firing in live play.** The
  logic reads correctly (full-row detection, 100/300/500/800 × level,
  back-to-back and combo) but nobody has actually cleared a row yet.

**Note for testing:** synthetic `KeyboardEvent` dispatch does NOT drive these
games — only real key events do. Automated testing has to go through the browser's
input layer, not `dispatchEvent`. The hidden `.pbtn` touch buttons DO respond to
synthetic `PointerEvent`s, which is a much cheaper way to drive a game from a
script than one tool call per keystroke.

### Voidrunner — the 3D one

Everything else here is 2D canvas, and Apex Run is *pseudo*-3D. Voidrunner is real
WebGL2: hand-written GLSL, its own matrix and quaternion maths, geometry generated
into typed arrays at runtime.

- **MRT bloom** — scene renders to a two-attachment FBO (colour + emissive) in
  RGBA16F via `EXT_color_buffer_float`, with an automatic RGBA8 fallback if the
  framebuffer comes back incomplete. Emissive is blurred half-res across four
  9-tap gaussian passes and composited additively.
- **Shading** — directional light, back-fill, specular, a distance-attenuated
  headlight pool sliding over the walls, fresnel rim on the ridges, emissive ribs
  antialiased with `fwidth`, exp-squared fog to `#0b0f1e`.
- **Camera** — built as a world matrix from a slerped quaternion then inverted, so
  position lag and orientation lag tune independently. That is what makes it bank
  and swing instead of feeling bolted to the ship.
- **5 draw calls** for all dynamic objects via `drawElementsInstanced`; canyon
  chunks stream through a pool of 13 reused VAOs.
- **Corridor safety audited at startup** — 80,000 samples, logging the true
  minimum clear radius (9.50 against a 1.15 ship radius). Rock bumps are built to
  be strictly ≥ 0 so they can only push walls outward.

Verified in-browser at 61.5 fps, clean console, `HDR targets: true` (so it runs
the float path, not the fallback).

**Not verified:** gamepad (no controller attached) and audio output. **Known
limits:** bloom is unthresholded — it blurs the emissive buffer directly, so
non-emissive highlights never bloom; and there is no MSAA, because the off-screen
MRT path rules out the default multisampled buffer. Edges are aliased, but the
neon glow dominates the look.

## Running locally

```
dev-serve.cmd
```

Serves this folder at <http://localhost:3020/> (also registered as the `games`
entry in `.claude/launch.json`). Use a real HTTP origin rather than opening the
file directly — `file://` breaks `localStorage` and the Gamepad API in some
browsers.

## Deploying

```
vercel deploy --prod --yes --scope o-connor-family
```

Run from this folder; it is linked to the `overclock-arcade` project. New projects
in this Vercel team are created with Vercel Authentication ON, which 401-locks
the public URL — it has already been turned off for this one, but check after any
project-level change.

## Installing it on a phone (no app store)

Open the link in Safari or Chrome on the phone, then **Share → Add to Home
Screen**. It gets its own icon and launches full screen with no browser chrome —
close enough to a native app that a kid cannot tell, for $0 and with no review
process.

The pieces that make that work, and the traps in them:

- `manifest.json` at the root and a second one in `apex_run/`, so adding either
  page lands on the right `start_url` instead of dumping you at the arcade index.
- **iOS ignores the manifest's icon list for Add to Home Screen** — it uses
  `<link rel="apple-touch-icon">` and the `apple-mobile-web-app-*` metas. Both
  sets have to be present or you get a blank square on the home screen.
- `apple-mobile-web-app-status-bar-style=black-translucent` runs the page under
  the status bar, which is only safe because the HUD pads itself with
  `env(safe-area-inset-*)`. Remove that padding and the lap counter goes under
  the clock.
- Icons are generated, not hand-drawn: `icons/` is produced by rendering an SVG
  through the repo's Playwright at 180/192/512/32px. The source SVG and the
  generator live in the session scratchpad; if the icon ever needs changing,
  redraw the SVG rather than editing the PNGs.

Verified by fetching every icon the manifest and the iOS tags reference and
asserting a 200 with a real byte count — a 404 icon is the usual reason an
"installed" web app shows a blank tile.

## Controls

| Action | Keyboard | Controller | Touch |
|---|---|---|---|
| Accelerate | Up / W | R2 or Cross | GAS |
| Brake | Down / S | L2 or Circle | BRAKE |
| Steer | Left / Right, A / D | Left stick or d-pad | ◀ ▶ |
| Confirm menu | Enter / Space | Any trigger | Tap |
| Pause | P or Esc | — | — |
| Mute engine | M | — | — |
| Restart race | R | — | — |

Controller support uses the standard Gamepad API, so any controller the browser
maps as "standard" works. Touch buttons appear automatically on coarse-pointer
devices.

**Bluetooth or USB — both work, and the button indices are the same either way.**
A DualSense pairs to Windows 11 as a plain HID gamepad with no driver: hold the
**PS button + Create button** (the small one left of the touchpad) until the
light bar double-flashes, then Settings → Bluetooth & devices → Add device →
Bluetooth. It usually appears as "Wireless Controller". What Bluetooth does *not*
carry on Windows is the controller's own speaker and headphone jack; haptics and
adaptive triggers are unavailable to a browser over either connection, so nothing
here depends on them. USB is only worth preferring because it charges while you
play.

The browser will not report the controller at all until a button is pressed on
it while the page has focus — that is a Gamepad API privacy rule, not a bug, and
it is why the menu says to press a button to bind it.

## How Apex Run works

The road is a list of 3,000–3,800 segments, each holding a curve amount and a
world height. Every frame the visible segments are projected to screen with a
simple perspective camera and drawn near-to-far as trapezoids; curves are faked
by shifting each segment sideways by an accumulating offset as it is drawn. This
is the classic pseudo-3D technique — there is no 3D geometry anywhere.

Rivals and traffic are the same kind of object and share one avoidance routine;
the only differences are that rivals hold a target pace and are ranked. Race
order comes from `progress` (total distance covered, laps included), not from
position on the track.

Things worth knowing before changing it:

- **The sky is drawn *after* the road**, into the strip above the topmost road
  pixel actually rendered that frame. Estimating a horizon instead leaves a
  hard-edged band on screen, because hills and occlusion change how far up the
  screen the road reaches on every frame.
- **Everything that moves the player goes through `movePlayerTo()`.** Collisions
  rewind `position`, and the lap counter and race order both read
  `playerProgress`; changing one without the other desyncs them. An earlier
  version compared start-of-frame to end-of-frame position and scored a
  collision as a completed lap — a 19-second lap on a 60-second track.
- **Rivals accelerate from a standstill like the player does.** Launching them
  at full pace drops the player to last in the first five seconds of every race,
  before they have done anything wrong.
- **The overlay is rebuilt from a string every time it is shown**, so button
  handlers live in one delegated listener on `#overlay`, not on the buttons.
- **Saved state:** best lap per track under `apexRunBest_<trackId>`, the
  championship under `apexRunChampionship_v1`. Bump a key if a change
  invalidates old values. All reads are wrapped — private-mode browsers throw on
  `localStorage`.

### Adding a track

Add an entry to `TRACKS` with a `build()` that calls the `addStraight` /
`addCurve` / `addHill` / `addSCurves` / `addBumps` helpers, and finish with
`addDownhillToEnd()` so the circuit closes back to zero height. Add a matching
palette to `THEMES` if it needs its own look. Aim for roughly 3,000–3,800
segments: that is a 50–65 second lap flat out and 90–120 with traffic.

## Checks

Both files pass the repo device matrix:

```
node .tools/responsive-check/check.js 29_games/apex_run/index.html
node .tools/responsive-check/check.js 29_games/index.html
```

`apex_run` reports a "floating elements over content" warning at phone sizes —
that is the intended full-screen game canvas plus its touch buttons, not a bug.

There is no automated test for the racing itself; it was verified by driving it
in headless Chromium — start a championship round, drive it, jump to the final
metres, and assert the finishing order, the points awarded and that round two
loads a different track and theme.

### Full-arcade sweep and Null Sector completion 2026-08-18

Every game was run end-to-end in headless Chromium (desktop) and headless
WebKit (iPhone 13 viewport, portrait AND landscape) with the new harness at
`.tools/game-playtest/playtest.js` — WebKit because it is the closest engine
to real iOS Safari that runs on a PC. The harness loads each game, verifies
requestAnimationFrame is actually firing, starts a run, holds a movement key,
samples the canvas to prove frames change, and checks for sideways overflow
and console errors.

Results: **no horizontal overflow in any game in either orientation**, no
console errors, all games start and animate on all three profiles. Voidrunner
cannot be play-tested headless (WebGL context loss under SwiftShader — it runs
fine in a real browser); everything else passes by machine.

Learned the hard way while testing: these games all pause when their tab
stops compositing (RAF stops + the visibilitychange auto-pause). Testing
through a hidden/occluded browser window produces false "the game is frozen"
diagnoses — playtest headless, where compositing never stops, or keep the
window visibly fronted.

Fixed in passing:

- **Apex Run menu:** `.tname`/`.tdesc` were inline spans, so every quick-race
  card ran its title straight into its description ("RidgelineRolling
  hills…"). Now `display: block`.

**Null Sector finished.** The file had the whole simulation (89 functions:
enemies, bosses, floor gen, shops, items) but no render layer, no frame loop,
and no `startRun`/`nextFloor`/`togglePause` — it crashed on any Start press.
Built the missing half in the same style as the rest of the file:

- Frame loop with the house dt-clamp, hit-stop and GC-pause slow-mo hooks.
- Full canvas render: tiled rooms with floor tints per FLOORS entry, barred
  vs glowing doors, distinct silhouettes for all nine enemy kinds + bosses,
  pedestals with names and prices, coins/hearts, the exit port, damage
  numbers, HUD (hearts, credits, floor, active-item cooldown), minimap that
  reveals as you explore, boss HP bar, banners/toasts, touch-stick overlays.
- Room flow: enter/clear/door logic, fade transition between rooms, port to
  the next floor, KERNEL PANIC death card, SECTOR PURGED win card, pause.
- **Door funneling** (found by scripted play, not by reading): walking into
  the wall beside an open door used to just grind — doors only worked when
  pixel-aligned, which feels broken on a thumbstick. Pressing toward a wall
  near an open door now pulls you sideways onto the mouth.

Verified by scripted runs: shop purchase debits credits and grants the item,
SEGFAULT boss dies and opens the port, the port loads floor 2, the floor-6
boss kill flips the run to the win screen, and dying shows the death card —
all with zero console errors.

**Ember and Null Sector are now on the hub.** Ember was already complete
(22 levels, tutorial hints, touch controls) and passes the sweep on all
three profiles — it just had never been listed.

### Built 2026-08-18 — Kilobyte, and the hub became a library

**Kilobyte** — the maze-chase slot the arcade was missing. Original 19x21
board (152 bits, four ROOT ACCESS nodes, side tunnels that wrap), validated
by flood-fill so every bit is provably reachable. The four daemons run the
four classic brains: SIGKILL targets you, SPOOF aims four tiles ahead,
FORK mirrors SIGKILL through your position, LURK hunts at range and flees
up close — on a scatter/chase mode clock that reverses everyone on each
flip. Root access flips them frightened (shrinking duration per level),
eaten daemons pay 200/400/800/1600 and walk their eyes back to the pen.
Payload chips at 70 and 140 bits, extra life every 10,000, grid movement
with buffered turns so cornering feels right, swipe steering on phones.
Verified by scripted play: eating, fright, daemon-eating with eyes return,
death/respawn, and board-clear all confirmed with zero console errors, on
desktop Chromium and WebKit iPhone portrait + landscape.

One render fix found by screenshot, not by reading: off-board neighbours
count as wall for movement (correct) but were also drawing eastward/
southward wall stubs off the board edge. Draw checks are now bounds-aware.

**The hub is now a game library.** Every card carries procedurally drawn
cover art (same no-assets rule as the games), your best score read
defensively from each game's own save (a missing or unreadable save just
reads "Unplayed"), NEW badges, category filter chips, and a played counter.
Zero horizontal overflow on desktop and iPhone in both orientations.

### Built 2026-08-18 (later) — Downlink

The Missile Command slot. Hostile packets streak down toward six server
nodes; three uplink batteries (the centre one throws faster interceptors,
as tradition demands) fire at wherever you click, and the shot blooms into
an EMP burst that does the actual killing — leading the target is the whole
game. MIRVs fork partway down, smart bombs sidestep blooms from wave 6, a
drone crosses the sky dropping warheads from wave 3, and raids also target
your batteries: a hit zeroes that battery's ammo for the wave. Wave tally
pays 5x per unused interceptor and 100x per surviving node (both scaled by
the wave multiplier, capped at 6x), and every 10,000 points banks a spare
node that is spent rebuilding after the wave. Keyboard picks batteries
explicitly (1/2/3), or auto-picks the nearest armed one; on a phone you
just tap where you want the bloom.

Tuned by scripted play: the first cut's warheads took 25+ seconds to fall,
which read as slow-motion rather than menace — fall speed roughly doubled.
Verified: interception scores, ground hits kill exactly the node they land
on, battery hits zero ammo, tally math pays out, wave 2 re-arms, and losing
every node ends the run — zero console errors, desktop + WebKit iPhone
portrait and landscape, no overflow.

### Built 2026-08-18 (later still) — Overflow

The snake slot, and the pun wrote itself: you are a buffer, packets append
to you, and writing past the fence or into yourself is a buffer overflow.
23x15 board that rotates 90° on portrait phones so the play area stays big,
speed tier rises every 8 packets (10 pts x tier per packet), a purple bonus
glitch worth 25 x tier + 50 appears on a timer and blinks out, turns are
buffered three deep with reversals rejected, and steering is arrows/WASD,
swipe, or gamepad. Head wears eyes that look where it is going, and the
gaze rotates with the board — the first cut looked the wrong way on phones.
Verified by a greedy autopilot: eat/grow/score/speed-tier all fire, and its
inevitable wall crash produced the BUFFER OVERFLOW card on cue. Zero
console errors, zero overflow (the layout kind), all three device profiles.

### Built 2026-08-18 (night) — Deadlock, the fighter

The Street Fighter slot, requested by name — and the arcade's first
two-player game: VS CPU, or two humans on one keyboard (P1 WASD+FGH,
P2 arrows+KL;). SYN (faster, throws a PING packet bolt) versus ACK
(heavier, dashes a SLAM uppercut). Best of three, 60-second rounds.

The systems that make a fighter feel like one: hold-away blocking with
real chip damage, hitstun and blockstun, meter that builds on giving AND
taking (50 buys your special), knockdowns with wakeup invulnerability via
the down/getup states, jump kicks, crouch that ducks projectiles, corner
pushback, and fighters that cannot walk through each other. The CPU ramps
per round and per win streak: it blocks reactively, sidesteps or jumps
PING, and spends its own meter.

And the Mortal Kombat moment, by request: take the deciding round and
instead of a KO the screen goes dark, both fighters get spotlit, and
FINISH THEM pulses in red while your opponent wobbles helpless. Land any
hit inside five seconds and it becomes a FATAL EXCEPTION — the loser
derezzes into ninety glowing shards. Hesitate and they merely collapse,
and the match card notes you did not earn the flawless.

Fighters are drawn as parametric neon skeletons — two-segment limbs with
per-state posture curves (walk cycles, punch extension, slam windup,
dazed wobble), a chest core light, and a visor that turns red when dazed.
No sprites anywhere.

Verified by scripted play: clean punch = 6 damage +11 meter, blocked
punch = 1 chip, PING = 50 meter for 14 damage and a knockdown, round win
-> round 2 -> FINISH THEM -> finisher -> 77-shard derez -> match card,
and the mercy timeout ends the round without re-triggering the finish
sequence (the first cut looped it — caught by reading, fixed before it
shipped). Zero console errors, all three device profiles, no overflow.

### Built 2026-08-18 (late night) — Airlock

Air hockey, built because the arcade needed a game two people can play on
one phone. On touch it is true multitouch: each player drags their own
mallet with their own finger, each finger locked to its own half. On a
desktop it is WASD against arrows, or mouse against the CPU. The table
stands upright on portrait screens and lies on its side on landscape ones
— the simulation always runs in upright table space and only the renderer
(and the pointer math) rotates, so the physics cannot tell the difference.

Physics: circle-circle mallet/puck collision with mallet velocity
transfer, four fixed substeps per frame so a slammed puck cannot tunnel
through a mallet or wall, air-table friction, a speed cap, goal mouths cut
into the end rails. First to seven, GAME POINT warning, serve alternates
to whoever conceded. The CPU intercepts the puck's projected path (wall
bounces folded in), comes around behind pucks pinned on its goal line
rather than pushing them in, and ramps with your win streak.

Also fixed in the harness while shipping this: unquoted Playwright text
selectors are substring matches, so `text=VS CPU` was clicking the help
row reading "Mouse (vs CPU)" instead of the button and the playtest
reported a false start. Selectors are exact-match quoted now; verified
with a trusted-input trace that real clicks land on the real button.

### Built 2026-08-19 — Defrag and Airtime

**Defrag** — the match-3 that completes the original wish-list. Eight by
eight, six sector types drawn as distinct shapes AND colours so
colourblind players are not guessing, no-match-at-deal board generation,
cascade chains with mounting multipliers, match-4 forging a scanline bolt
(clears its row or column when consumed), match-5 forging a colour purge,
quota-per-level against a shrinking move budget, a hint that sparkles
after four idle seconds, and an automatic reshuffle whenever the board
has no legal move.

**Airtime** — built to the request "a dirtbike game that has jumps."
Gravity Grip already owns the survival ride, so this one is the trick
game: three authored courses (SANDBOX SX, RIDGE RALLY, BIG AIR CANYON)
assembled from kickers, tabletops, doubles, step-ups and whoops on a
sampled heightfield. Grounded physics run along the surface; leave a lip
and you are a projectile with rotation control — full rotations count as
flips (+700 x combo), landings are judged by angle against the slope:
square within ~12 degrees is CLEAN (+250, combo up), within tolerance
keeps the points, past it is WRECKED — tumble, combo gone, back to the
last checkpoint. The scripted test bot held the flip key all flight,
over-rotated and got wrecked, which is exactly the correct outcome.
Engine audio is a pulse wave that climbs with speed and jumps a fifth
when you leave the ground.

### Built 2026-08-18 (small hours) — Tilt and Solitaire

**Tilt** — pinball, and on request it grew from one table to three before it
ever shipped. Segment-based collision (walls and slingshots as line
segments, bumpers as circles, targets as boxes with per-table kick
directions), five fixed substeps per frame so the ball never tunnels, and
flippers modelled as rotating capsules whose surface velocity at the
contact point is what launches the ball — flip timing genuinely matters.
Three tables on one physics engine: BOOT SECTOR (cyan, bumper triangle,
left bank), HEATSINK (orange, four-bumper diamond, V-baffle fins, right
bank), MOTHERLODE (green, crown bumper over a walled island vault,
horizontal target bank that kicks upward). Every table has its own
multiball name, rollover letters, and saved high score. Ball saver,
slingshot kicks, and a nudge system: three nudges in one ball and the
machine TILTs — flippers dead until you drain, as is right and proper.

**Solitaire** — Klondike for the family crowd. Procedurally drawn cards
(no images), draw-1 or draw-3 chosen at deal, tap a card to send it
somewhere sensible or drag it (whole stacks move together), unlimited
undo implemented as full-state snapshots, and once the stock is empty and
every card is face up an AUTO button appears and plays the endgame with a
satisfying tick-tick-tick. Wins and best time persist. The win screen is
preceded by the obligatory bouncing-card cascade.

Also taught the playtest harness that a card game's canvas is
legitimately still between moves — a `staticOk` flag skips the
animation check that every action game must still pass.

### Built 2026-08-18 (later that night) — Overdrive, for Amber

The Crazy Taxi slot, requested by name for Amber. A gold checker cab loose
in a procedurally generated 8x8-block neon city: roads on a grid, blocks
subdivided deterministically into one-to-four buildings (same city every
run — landmarks stay learnable), parks with tree clusters, named districts
(CACHE HEIGHTS, HEAP SIDE, PIPELINE ROW...) that fares actually quote.

The Crazy Taxi loop: riders glow green on the curb and wave; stop beside
one and they board with a destination, a fare, and a timer. A gold arrow
orbits the cab pointing at the beacon with live distance. Deliver with
more than half the timer left and it rates CRAZY (+60% tip), over a fifth
GREAT (+25%), else OK — and every delivery buys clock back, so a good
run snowballs. Dawdle and the fare bails, no pay. Global clock hits zero,
shift over, best earnings saved.

Feel: arcade drift physics — grip kills sideways velocity unless the
handbrake loosens it, skid marks accumulate and fade, walls are slid
along rather than face-planted (axis-separated collision), traffic
shunts you and honks, and the engine is a live sawtooth through a lowpass
whose pitch and gain follow your actual speed. Buildings render 2.5D:
roofs lean away from the camera by their height, walls fill the gap,
lit windows scatter deterministically.

Two bugs out of the build, one by reading and one by screenshot: a junk
line doubled the sideways-grip correction on one axis (read), and the
roof-parallax offset was scaled twice, flinging rooftops hundreds of
pixels off their buildings so half the city read as black voids
(screenshot). Verified by scripted play: driving, wall sliding, pickup,
delivery with clock bonus, fare bail, and time-up ending — zero console
errors, all three device profiles.

### iPhone placement audit 2026-08-19 — all 22 games, both orientations

New tool: `.tools/game-playtest/ui-audit.js` — loads every game in WebKit
iPhone portrait AND landscape, geometry-checks every visible control
(on-screen, ≥40px, no pairwise overlap) at menu and in play, and
screenshots both states for eyeballing the canvas-drawn HUD.

All twelve 2026-08-18/19 games passed untouched. Five fixes in the older
files, all found by the audit:

- **Voidrunner:** touch buttons (BOOST/FIRE) showed under the title menu,
  overlapping LAUNCH — touch UI now gated behind a `playing` class like
  every later game. Menu keys list hidden on short screens; overlay made
  scrollable as backstop.
- **Deep Run:** landscape menu buried LAUNCH below the fold (usable
  landscape height on an iPhone is ~342px, not 390). Keys/legend hidden
  and paddings tightened under `max-height: 620px`; LAUNCH now sits 58px
  clear.
- **Starfall:** 38px icon buttons → 44px.
- **Firewall:** 36px-wide speed/pause/mute → 44px, stepping down to 40px
  under 420px width so the row never clips the edge.
- **Deadlock:** the P2 health bar and name ran under the mute/pause
  buttons; bars now clear both the button zone and the centre clock at
  every width.

Also new: `GAME-RULES.md` — the build law distilled from all 22 games
(skeleton, loop, layout zones, audio, saves, feel, verification pipeline,
and the do-not-relearn trap list). Read it before starting game 23.

### Built and play-tested 2026-08-18 — Botnet (game 22)

The fixed-shooter slot — Space Invaders by way of Galaga — was the last
big classic missing from the shelf, and the name was sitting right there.
BOTNET: the swarm found your machine, and every bot you drop is one node
off the net.

Built to GAME-RULES.md as the first game after it became law, and it held:
skeleton copied from Downlink, fluid full-screen strategy, all three input
paths, cards fit 342px. This one is also the graphics showcase Krystal
asked for — drifting nebulae behind a three-layer falling starfield,
two-frame wing-flap animation on every bot (each of the four types has its
own silhouette: saucer drone, segmented worm, armored brute, crowned
harvester), bezier entry choreography in alternating six-bot squads, dive
thrusters, muzzle flash, shockwave rings, particle bursts, slow-mo on
harvester kills, and a kill-chain readout.

Scripted play beat all of it before ship: 20 assertions covering the core
loop, a forced dive kill, the SPAM ship, wave clear into wave 2, the
extra-life threshold, player death, respawn invulnerability, game over
with save, restart, and pause — zero console errors, all three device
profiles clean, ui-audit clean both orientations.

Found by eyeballing the play screenshots, not by the geometry checks:

- **The formation hung off both screen edges.** Column spacing was scaled
  per-row off the row's own count, and the widest rows spanned ~1.26x the
  screen — the outer bots clipped in half at every width. Spacing is now
  uniform, derived from the wave's widest row, and capped so formation +
  sway + breathe stays inside the screen with margin.
- **The lives icons sat inside the formation's top row in landscape**
  (row 0 lands at ~51px on a 342px-usable screen, lives drew at 58px).
  They now draw inline after the HIGH readout on the second HUD line.

(Count correction, found while listing the hub: the running "22 games"
tally we had been carrying was off by one — at the previous commit the
hub and this table both held 21 games. Botnet is game 22.)

### Graphics pass 2026-08-18 — Neon Breaker, Gridlock, Deep Run

Krystal asked for better graphics across the board, so the three oldest
games got retrofitted with the juice vocabulary the newer games shipped
with. Gameplay untouched — every change is presentation.

- **All three:** drifting nebula colour fields behind the action (the
  Botnet backdrop treatment), and hit-stop slow-mo on the biggest moments.
- **Neon Breaker:** bricks now visibly break apart into spinning debris
  shards with gravity; explosive bricks land a hit-stop and an orange
  screen flash; losing a ball slows the world and flashes red; each level's
  bricks cascade in row by row instead of just appearing.
- **Gridlock:** an animated three-layer falling starfield behind the well;
  line clears fire a shockwave ring per row (gold on a quad, which also
  slows the world for a beat); hard drops kick dust off the landing edge
  with a nudge of shake.
- **Deep Run:** shockwave rings on every explosion, shield pop, and
  threaded near-miss; ship deaths now fire a double ring (gold + white)
  and play out in slow motion.

Verification: all changed paths beaten by script, not read — Gridlock's
clear path via a route-injected test hook driving a REAL single clear and
a REAL quad (4 rings + slow-mo asserted), Deep Run's death via a 25ms
in-page watcher that caught the transient slow-mo (a first attempt polled
at 150ms and missed the whole 0.5s effect window — sample faster than the
effect you are asserting). Full 3-profile matrix and ui-audit clean on all
three, zero console errors. One design gap caught by the watcher: rock
deaths (the common kind) had no shockwave because only explode() carried
rings — killShip now fires its own.

### Graphics pass 2026-08-18/19 — the remaining six older games

Second half of the better-graphics request: every pre-Downlink game is now
at the current juice bar. The kit was fitted to each game's fiction rather
than pasted on — a racer does not want a nebula, and a circuit board does
not want stars.

- **Starfall:** parallax nebulae behind the grid (they drift with the
  ship), and player death now joins the boss kill in slow motion.
- **Apex Run:** stars in the sunset and night skies (dawn stays clean),
  crash shake + red impact flash on scenery and traffic collisions, and
  speed streaks past 65% throttle. No slow-mo — a hit-stop mid-race
  feels like lag, not drama.
- **Gravity Grip:** nebulae over the ridge line, and crashes fire a
  gold + white double shockwave. The rings age in sim-time, so they
  expand in slow motion during the existing 0.14x crash — that is
  deliberate, and the test had to learn to wait for it.
- **Firewall:** a downed ROOTKIT now lands a double ring and a beat of
  hit-stop. The circuit-board backdrop was left alone on purpose.
- **Flyway:** every dropped bird fires a shockwave (gold for bolting
  birds), and the marsh holds its breath for a beat on the dramatic
  shots — a bolting bird, or the shot that empties the sky.
- **Voidrunner (WebGL):** damage hit-stop only — pure dt-scaling, zero
  GL changes, because a WebGL regression can be GPU-specific and this is
  the one game the headless harness cannot run. Verified in a real
  fronted browser: slowT spikes to 0.14 and decays clean, zero console
  errors, 752m test flight healthy.

All five 2D games script-verified through the injected-hook rig (real
crash, real boss kill, real duck kills asserted), full matrix + ui-audit
clean, zero console errors everywhere.

### Built and play-tested 2026-08-19 — Quadcore and Prom (games 23 and 24)

Two requests from the kids' department in one evening: "a fourwheeler
game" and "a princess game / barbie game."

**Quadcore** — a four-wheeler is a quad, and four cores racing is the
name doing itself. Top-down night-trail racing: Catmull-Rom loops built
from seeds (same trail every time, per track), one shared physics
function for player and AI (forward/lateral velocity split, grip model,
mud drag, ramp ballistics), rubber-banded rivals, and a forest that is
actually solid — trees push back. Scripted play beat the whole race:
pickups, mud, ramps, three laps, the finish, the saved track record.

**Prom** — she is the Princess of the ROM kingdom, and PROM is a memory
chip; the pun holds. Named with care: the request said "barbie game,"
but Mattel owns that word, so the arcade got an original princess
instead — what she IS is the barbie game: a dress-up studio (skin, hair,
crowns, four gown silhouettes, colours, sparkles, shoes, extras — every
tap chimes a pentatonic note and persists), then GO TO THE BALL: a
spotlight walk into the ballroom, a procedural 3/4 waltz, twirls, real
fireworks, confetti, hearts, and a court that claps. No timers, no
failing, nothing to lose — the first pure toy on the shelf, and the
first game in the new Kids category on the hub.

Found by eyeballing, not by the geometry checks:
- **Quadcore's grass was as fast as the trail** (drag constants), trees
  were decoration you could drive through, and the off-trail world read
  as black void. Grass now costs real speed, trees are solid with a
  thump, and the forest floor got mottling.
- **Prom's court guests were mouse-sized** next to the princess and the
  chandeliers were faint wire. Guests are now proper-sized courtiers in
  gowns and coats who clap; chandeliers got gold frames and candle glow.
- **Landscape ran the EXTRAS tab under the mute button** — the panel now
  reserves the icon-button zone, per the layout law.

### Built and play-tested 2026-08-19 — Scope (game 25)

Krystal asked for "a hunting game with deer and turkey" and, mid-build,
"make it more realistic not neon." So SCOPE (a rifle scope; a variable's
scope) became the arcade's first naturalistic game: muted dawn palette,
layered pine-and-oak treelines in haze, mist bands that burn off as a
procedural sun climbs, songbirds between shots, crows that lift off the
treeline when you miss. Zero glow anywhere.

The scope is the trick: the whole scene draws twice per frame — once
plain, once scaled 1.7x inside a clipped lens circle around the aim
point, under a duplex reticle. Sway is summed sines; holding breath
calms it to a whisper while a heartbeat thumps, and running the meter
dry forces a heaving pant. Ethics tuned for the family: no wounded
animals ever, one shot spooks the whole field, and CLEAN HARVEST x2
only comes from calm, feeding animals — patience is the whole game.

Found by playing and eyeballing, not by reading:

- **A leaked canvas save() in the deer's new skull transform ate the
  entire scope lens, the HUD, and a doe** — everything drawn after the
  first buck inherited his body transform and rendered off-canvas, with
  zero console errors and a healthy RAF. The screenshots caught it;
  nothing else could have. Count your save/restore pairs.
- **The world outside the lens was 90% black** — realistic for an eye
  down a scope, unplayable for finding animals. It now dims to ~42%.
- **The first deer read as a table with an egg on it.** The neck needed
  filled mass (a wedge, not a stroke), the head needed to be one
  tapered skull-plus-muzzle shape, and the white tail flag belonged
  small and at the rump, not floating over the shoulder.

### Built and play-tested 2026-08-19 — Cast (game 26)

"A fishing game." CAST — you cast a line, code casts a type — is Scope's
sibling: same naturalistic direction, a Carolina pond at golden hour that
slides into dusk over three minutes, crickets thickening as the light
goes, early stars, dragonflies, a quiet angler silhouette on the dock.

One button is the whole interface, context-sensitive: hold to charge the
cast (with a dotted arc preview), release to fly, tap inside the bite
window when the bobber dips, then hold to reel against a live tension
model — fish runs spike the tension, the rod bends, the line turns red,
and holding on past the limit snaps it. Fish have species AI: bluegill
shallow and bold, crappie over the brush, bass off the weedline (warier,
and they jump mid-fight), cats deep and heavy. Wariness, approach,
inspect, bite-or-drift-off. A rare hookset is just an old boot.

Scripted play beat every path: charge/cast/soak/sink, a forced bite and
hookset, tension up while reeling and line gained, tension decay on
release, a landed catfish on the stringer, an over-tension snap-off, the
boot scoring nothing, dusk ending the evening into the tally, and both
saves. One rig lesson repeated from Quadcore: a bite can only exist while
the rod is soaking — the first snap/boot tests forced bites on an idle
rod and hookset() rightly refused.

### Built and play-tested 2026-08-19 — Smash (game 27)

"A monster truck game." SMASH — smashing the stack, smashing a minivan.
Freestyle night in a stadium: crowd banks that bob harder when your
combo is hot, floodlight towers with cones, a dirt floor with tire ruts,
and a truck that is mostly suspension: two sprung wheels under a rigid
chassis, fixed-step physics at 120Hz, gas leans back in the air and
brake noses down, exactly like Gravity Grip taught us.

Three bugs found by script and trace, none by reading:
- **A leftover `this._ = 0` line threw on every physics step** under
  strict mode (plain-call `this` is undefined) — the truck sat frozen at
  the start line while the page reported a healthy title screen.
- **The truck self-righted from fully upside down.** Two causes, found
  by tracing the angle over time: the auto-level torque had no upright
  gate, and — the good one — the suspension torque used the upright
  lever sign (`force * wheelSide`), so with the truck inverted the
  contact force torqued it back over the top. The fix is physics: torque
  about the REAL lever arm, `force * (contactX - centerX)`. A wrong sign
  convention turned the suspension into a self-righting motor.
- **The wheels smeared diagonally whenever the truck rotated** — they
  were drawn inside the rotated body frame using world-vertical offsets.
  Wheels render in world space now, hanging off the chassis side even
  mid-flip.
- **The rollover timer reset on every spring bounce** — an inverted
  truck bouncing on its own wheels never accumulated the 0.7s. The
  timer now decays instead of resetting.

Scripted play beat: driving, three crush stages on a junker, a full
flatten, a launched backflip landing for points, the combo chain inside
its window, three rollovers ending the show, the timer ending it too,
saves, and pause.

### Built and play-tested 2026-08-19 — Chip and Patch (games 28 and 29)

Two games built in parallel by separate builders, each confined to its own
folder, then re-verified and integrated here. The hub also grew proper
**Sports** and **Outdoors** shelves — at 27 games "action" had become a
junk drawer.

**Chip** is nine holes of putt-putt on a naturalistic course: mowed
stripes, weathered rails, sand that reads as sand and water that reads as
water. The board rotates 90 degrees in landscape so a phone held either
way gets the whole hole.

**Patch** is the second toy on the Kids shelf beside Prom — a cottage
garden that cannot be lost, only tended.

Bugs worth recording, all found by playing or looking, never by reading:

- **Chip's flagstick was drawn in world space**, so the moment the board
  rotated for landscape it lay flat across the green and read as a red
  hook in the grass. Screen space now, always upright.
- **Chip's lip-out was fake.** Per-substep damping bled a 900 u/s ball
  below the sink threshold *while it was still over the hole*, so hot
  balls dropped anyway. A latched flag now lets entry speed decide the
  whole pass.
- **Chip indexed `HOLES[9]` after the ninth hole-out** and threw every
  frame behind the scorecard — invisible in source, an error flood on
  screen. Verified fixed here by playing a full round out: nine sinks,
  scorecard, save, zero errors.
- **Patch's tilled soil read as wooden decking** (aligned full-width
  furrows), its fence posts ran like scaffolding through the beds, and
  its butterflies vanished at the bottom of every wing flap.

And one lesson about verification itself: the integrator's first
containment test for Chip reported a clean pass over 18,000 frames while
also flooding 18,000 canvas errors. Both numbers were wrong — the test
called the exposed `place()` helper with no arguments, wiping the ball's
position to `undefined`, so every `legal()` check was comparing NaN and
trivially passing. Re-run against the API correctly (`setHole` → `aimAt`
→ `strike`), it is a genuine pass: 108 full-power shots across all nine
holes, 8,166 frames, never once through a rail, zero NaN, zero errors.
**A green test can be green for the wrong reason. Check that your test
touched what you think it touched.**

### Built and play-tested 2026-08-19 — Pitch (game 30)

The third of the parallel build, and the one that needed the most art
surgery. Ballistics were tuned in node before a line of render code was
written — 105 mph at 28 degrees carries 413 ft, which is right.

Bugs, nearly all of them screenshot-only:

- **A dead orange void filled a third of the screen**: the backdrop was
  drawn in screen-space fractions with nothing between it and the ground
  line. Rebuilt as a world-anchored grandstand at its own perspective
  scale.
- **Infield dirt circles became tall skinny lakes on every fly ball** —
  the ellipse radii scaled on different axes, so the shape only broke
  once the camera pulled back. Invisible standing at the plate.
- **The camera never showed the fence.** You watched a 430-foot homer
  with no idea what it had to clear. The wall now reveals as the ball
  passes 100 feet.
- **The catcher and umpire stood bolt upright** — the crouch geometry
  was there but knees weren't forward and hips weren't low, so they read
  as short men in masks. Rewritten as real squats, and the umpire
  straightens up to punch out a strike.
- **The swing chopped wood**: interpolating the bat from up-behind to
  down-in-front swept it through vertical. Contact got its own keyframe
  at a flat barrel.
- **The crowd read as a QR code** until it got aisles, empty seats and
  jitter.

Integrator verification: all four pitch types measured in flight and
confirmed distinct (0.64s/97mph through 0.96s/79mph — a hitter feels
that spread); a perfect swing produces BARREL at 102 mph and 33 degrees;
a mistimed swing is an out and never leaves the yard; ten outs ends into
the summary; the save round-trips (1 HR, longest 392 ft). Matrix and
audit clean, zero console errors.

That is **30 games**. The hub now shelves them as Action, Shooters,
Racing, Sports, Outdoors, Puzzle, Strategy and Kids.

### Built and play-tested 2026-08-19 — Spare, Grind, Cache and Parse (games 31-34)

Four built at once, each builder locked to its own folder and its own
scratch directory (the fix for last batch's collision, now §11 law).
Every one re-verified here before shipping — and in this batch the
integrator's independent checks were run against hand-computed truth
rather than the builders' own tables.

**Verified by the integrator, not taken on report:**

- **Spare's scoring**, against a known truth table: twelve strikes = 300
  with the 30/60/90 progression; nine-and-spare ten times = 190; all
  gutters = 0; strike-then-4-then-3 scores frame 1 as 17; both 10th-frame
  fill cases (X 7 2 = 19, 7/ 6 = 16) correct.
- **Parse's letter marking**, against marks worked out by hand: CRANE /
  EERIE marks exactly one E — the one in the right slot — with the
  leading E absent. Plus ALLOY/LLAMA, SPEED/ERASE, ABBEY/BABES. Its word
  list independently checked: 402 answers, all five lowercase letters, no
  duplicates, all present in the accepted set, none flagged unsafe.
- **Cache's third-card lock**: during the 0.8s mismatch window a third
  tap is refused and the pair flips back cleanly.
- **Grind's bail rule**: a bail zeroes the live chain and leaves the
  banked score untouched; a clean bank adds.

Bugs the builders found that no assertion could have caught — the
screenshot pass earning its keep for the fourth batch running:

- **Cache's moon rendered as a solid blob.** The crescent traced the
  wrong side of the inner circle, so the subtraction filled the disc.
  Every state assertion passed with it broken.
- **Grind's sky gradient was keyed to screen height**, so everything
  behind the park painted as orange sunset and the bowl read as a hole
  punched through to the sky. Its chain-link fence was also 3x too tall
  and its treeline grew out of the concrete.
- **Spare's aiming marker was scaled by near-camera perspective** and
  rendered as a 100px billboard covering the lane; its ball in hand sat
  behind the foul line and was painted over by the approach.
- **Parse's M and P keys were global mute/pause hotkeys**, so typing
  LLAMA silently muted the game and swallowed the M — the guess never
  submitted.

And one physics root cause worth keeping: **no strike was reachable in
Spare** until the pin solver moved from a fixed substep *count* to a
fixed substep *size*. At 47 ft/s a pin travelled more than its own
diameter per step and tunnelled straight through its neighbours. Strike
rate went 0% to 13% on that alone, then 31% once the hook was tuned back.

That is **34 games**.

### Built and play-tested 2026-08-19 — Sweep, Sprint, Type, Fragment, Scan (games 35-39)

Seven builders were launched at once and all seven died mid-flight on a
session API limit. Five had written a complete file first; two (SUM and
SYNTAX) never got past reading the house style. The five survivors were
drafts abandoned partway through their own verification — so they were
treated as untrusted and re-verified here from scratch.

Note for next time: **seven concurrent builders is past the budget.**
Four was comfortable; seven was not. Batch size is a cost decision, not
just a speed one.

Verified by the integrator, not taken on report:

- **Sweep** — 360 freshly generated boards across all three sizes: the
  first click was never a mine, the mine count was always exact, and the
  no-guess guarantee held on 100% of beginner and intermediate boards and
  96% of expert. The remainder fall back to a plain board after the
  repair cap, which is the designed safeguard against a hang.
- **Type** — the WPM and accuracy maths driven to exact known cases: 50
  correct characters in 30s is exactly 20 wpm, 200 in 60s is 40, and 45
  correct of 50 keystrokes is 90%. Pause/resume also works, which its
  builder had flagged as a suspected bug before it died.
- **Fragment** — screen wrap tested in all four directions: position
  wraps and velocity is preserved every time. Its builder died before
  taking a single screenshot, so every visual check here is the
  integrator's.
- **Sprint** — the core mechanic proven: alternating sides builds speed
  (1.12), while mashing one side decays it (0.53). Mashing must not work,
  and it doesn't.
- **Scan** — the no-speech fallback: with `speechSynthesis` forced
  undefined before any page script ran, the game still starts, still
  plays, and throws nothing.

All five pass the three-profile matrix and the control audit with zero
console errors.

That is **39 games**.


### Built and play-tested 2026-08-19 — Greedy (game 40)

Hungry Hungry Hippos, renamed for the house: a **greedy algorithm** takes
whatever is nearest and never looks back, which is exactly what four
daemons do to one shared buffer pool. Four jaws on four arcs, 24 packets
loose in the middle, five rounds, AI that gets sharper each round.

**The verification is the story here.** The browser pane in this session
never composited, so `requestAnimationFrame` never fired — the game read
as completely frozen: zero packets eaten, jaws at 0, daemons pinned to
their base angles after 24 seconds. That is the Starfall trap in §3 of
GAME-RULES, and it cost time again even though it is written down.
Fronting the tab did not help; RAF stayed at 0 frames.

So the sim was verified **headless in Node** instead —
`.tools/greedy-headless-test.js` stubs the DOM, canvas, audio and
localStorage, boots the real script, and drives the real `update()` on a
fixed dt. Fifteen checks: AI leaves its base angle, AI actually chomps,
the pool drains, scores accumulate, the player can score, rounds
transition, the match reaches round 5, no packet escapes the arena, none
stall dead, and a full clamped 0.05 step never flings anything. All pass.

Two of those checks failed on the first run and **both were bugs in the
test, not the game** — the player-scoring check ran after the AI had
already cleared the board, and the dt-clamp check called `update(5)`
directly when the clamp correctly lives in `frame()`. Worth stating
plainly, because a red check is not automatically a red game.

Kept from the house pattern: `window.__GREEDY` playtest handle (same
convention as `__FW`, `__GG`, `__FLY`), fluid full-screen arena sized off
`min(w,h)` so both orientations work without letterboxing, and the harness
lives in `.tools/` rather than the game folder so rule 1 — one folder, one
`index.html` — still holds.

Not verified here, and left for a real browser: the canvas art itself, the
three-profile responsive matrix, and the control audit. **Someone should
eyeball it on a phone before this is called done.**

That is **40 games**.

### Built and play-tested 2026-08-20 — Sum and Syntax (the maths and writing tutors)

The two learning games lost when the seven-agent batch died. Rebuilt as a
pair — two concurrent builders, not seven — and both finished cleanly.

**Sum** is a maths tutor, not a quiz. Seven skills from number bonds to
fractions, 589 individually-tracked facts, each taught with a visual
model: ten-frames, a number line you hop backwards along, place-value
columns with a "10 ones = 1 ten" rod, dot arrays, shaded fraction bars.
Every fact carries a Leitner box and a due counter, so weak facts come
back sooner and mastered ones fade; a working-set cap stops 65 solid
facts crowding out the one a child keeps missing. A wrong answer works
the model through and re-queues the fact.

**Syntax** is a sentence lab: capitals and end marks, fragments and
run-ons, building sentences from tiles, commas, apostrophes including the
its/it's trap, homophones in context, and editing a paragraph with
planted errors. Every wrong answer explains the rule in a child's words,
quoting that sentence.

Integrator verification — the content itself, re-derived independently
rather than trusted:

- **Sum**: all **589 facts** walked, every answer re-computed from first
  principles. Zero wrong. Carrying is genuinely required in every carry
  item and borrowing in every borrow item; no subtraction goes negative;
  every division is exact; and every fraction comparison names the
  genuinely larger fraction.
- **Syntax**: the capitals stage re-audited against independent rules —
  the words needing a capital are exactly the sentence opener, proper
  nouns and "I", with no common word wrongly capitalised, and every end
  mark matches its sentence type. Zero faults.

Both builders also found real content bugs themselves, which is the
point of making them audit their own data: Sum's fraction-compare bars
rendered **completely unshaded** in the ask state (a child asked "which
is bigger?" against two blank bars — invisible to every geometry check),
and its number line **labelled the landing tick before the answer was
revealed**, handing over the answer. Syntax's run-on detector mislabelled
two pieces of clean prose ("Sarah said we needed to give him a bath."),
which would have taught a wrong rule had a paragraph hit it.

A count correction while integrating: the hub and the folders were
reconciled directly and both hold **42 games**. The running tally in
these notes had drifted by one again — reconcile against disk, not
against the last number written down.

### Built and play-tested 2026-08-20 — Char (letters and sounds, built for Lizzy)

The first of three games built specifically for a four-to-five-year-old
who is **not yet reading**, and who has a significant medical history —
laryngomalacia, three surgeries by three months, a botched first repair
redone around six months, and possible resulting oxygen-related damage.
Her family's framing governs the design: bright kid, spent her life short
of air. So: **low floor, high ceiling** — and, in her father's words,
*"find her level, then help her grow."*

What that means concretely, and what was verified:

- **Nobody picks a difficulty.** Four activities (find the letter, big and
  little, what sound, first sound) each have an explicit rung ladder. The
  game places her invisibly by playing, promotes after four correct in a
  row, demotes fast after two misses in five to protect confidence, and
  silently probes one rung up every 15-20 items so she can never be
  trapped below her ability. The found rung persists — she resumes, she
  is never re-placed.
- **Integrator check of exactly that**: simulated children with true
  ability at rungs 0, 2, 4 and 6 were run 250 items each. Each settled at
  its own rung (0→0, 2→2, 4→4, 6→6), with the tail reaching one above,
  which is the probe working. It finds her level and holds it.
- **Nothing is ever marked wrong.** No red, no X, no buzzer, no shake, no
  score, no timer. Her tap is never marked; the right answer simply
  lights up with a rising two-note cue. The source comments say it best:
  *"the only two states: chosen-and-right, or here-is-the-one."*
- **Everything is spoken** (rate 0.85, key word echoed after a pause) and
  the game stays fully playable with `speechSynthesis` unavailable.
- **Targets**: answer tiles measure 178x298 on a 390px phone, speaker
  110x110 — far past the 90px floor, single taps only, no drag or
  long-press anywhere.

The builder's picture check is worth recording. It rendered all 22
procedurally drawn pictures into one gallery and looked at them, which
caught five a four-year-old would have misnamed — a moon that read as a
"C", a nest whose eggs were buried, a washed-out igloo that read as a
rock, a stubby octopus that read as a jellyfish, and an egg that read as
an ice-cream cone. Then a **van that read as a bus** — a genuine trap in
a game where /b/ is one of the sounds being taught. All redrawn.

Integrator note on verification itself: **four separate times today an
independent check failed for the wrong reason** — a helper called with
the wrong arguments, a selector that swept in the mute buttons, a grep
that matched code comments saying there is deliberately no wrong state,
and an `adapt(id, right, probe)` call passed a state object as its id.
A red result deserves exactly the same scrutiny as a green one.
