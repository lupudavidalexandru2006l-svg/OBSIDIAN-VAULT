---
created: 2026-10-30
tags: [ice-ray-for-pets, qa]
---

# Ice Ray for Pets · Prototype QA

Prototype QA before the port ([[QA Rules]] › 1). Three reviewers as subagents (play-tester, code auditor, design reviewer, [[QA Rules]] › 2), each finding with an id. Fixes logged with what, where and how they were checked (§ 9). Related: [[Games/Ice Ray for Pets/Port Plan]], [[Lessons]].

## Round 1 · commit 63483fe · NO-GO
| Reviewer | Blockers | Should fix | Small | Owner decisions |
|---|---|---|---|---|
| Play-tester (PT) | 3 | 4 | 11 | 3 |
| Code auditor (CA) | 1 | 8 | 7 | 1 |
| Design reviewer (DR) | 2 | 12 | 8 | 11 |

The blockers:
- **DR-01** the green guide arrow pointed away from the goal.
- **DR-02** nothing could ever melt (longest run home 17 s, shortest cube life 20 s).
- **PT-01** on phones the coin counter covered the Settings tile.
- **PT-02** a gamepad couldn't open menus or close a popup.
- **PT-03** the ice bridge ending under you left you stuck in the river.
- **CA-03** a bought Super Freeze cube was lost if you left before the pen.

## Round 2 fixes
| Id | What changed | Where | How checked |
|---|---|---|---|
| DR-01 | Arrow turned a half turn more (the chevron is modelled along -z) | `client.js` arrow | read the maths; screenshot |
| PT-01 | Screen layout moves the tile grid up and the coins down so they never touch; re-runs when the coins grow (the +N/s line) | `hud.js` layout | layout check 844×390: no overlaps (the dynamic thumbstick aside) |
| PT-02 | Gamepad: Start picks a tile, d-pad moves, A presses, B closes, Y presses the Super Freeze button | `input.js`, `hud.js` | gamepad run (see below) |
| PT-03 | When the ice bridge ends, anyone on it lands on the nearest bank ("Splash!") | `server.js`, `world.js`; Roblox `FreezeService` | bridge run (see below) |
| CA-03 | Bought cubes are saved with the purchase and come back on your back after a rejoin | `server.js`; Roblox `CarryService`, `DataService` | suite: "survives leaving and rejoining" passes |
| CA-01 | Movement budget on the server's own clock; every half stud of a move must be walkable | `server.js`, `world.js` | suite + exploit test "100 small steps in one tick" |
| CA-02 | Locked-zone pets can't be zapped; the Forest zone starts at the gate | `server.js`, `config.js`; Roblox `Config` | suite |
| CA-04 | Only the three real upgrade ids are accepted | `server.js` | suite + exploit test |
| CA-05 | "First carry home" needs a real trip out (4 studs) and also logs just before the first bank, so the funnel stays in order | `server.js`; Roblox `PlayerTracker` | 3 bot seeds: steps 1-8 in order |
| CA-06 | Forest zone starts at the gate (z 194) | `config.js`; Roblox `Config` | suite |
| CA-07, CA-08 | Board scores clamped (≤ 1 freeze a second since joining, caps in Config); weekly coins only for this week; rivals reset each week | `server.js`, `config.js` | suite |
| CA-09 | "Not yet" messages have a 2 s cooldown | `server.js` | suite |
| CA-10 | Super Freeze offer at most once per run (the flag rides through a re-freeze) | `server.js`; Roblox `CarryService`, `WildPetSpawner` | suite |
| CA-11 | Every save field type- and range-checked on load | `server.js`; Roblox `DataService` | suite (24 damaged saves) |
| CA-12 | The client sees copies, not live server objects | `server.js` view | suite |
| CA-13, PT-11 | "Reset save" leaves the URL clean, so a refresh keeps progress | `main.js` | play |
| CA-14 | Test-panel buttons built once; "joined" is counted | `main.js` | play |
| CA-15 | Shared pet geometry; removed pets and cubes free their materials | `client.js` | code read |
| CA-16 | Gift box opens after the first bank (the first minute stays on the core loop) | `server.js`, `client.js` | suite |
| DR-03 | While carrying, the camera rises and looks down more; a light pillar over your pen | `client.js`, `config.js` | screenshots |
| DR-04 | Pen holds 100 pets in the prototype; the Pen upgrade is a port item | `config.js`, Port Plan | bot: 100 pets at 900 s |
| DR-05 | A pet you hold Freeze on acts at half speed (the kept pose is still the one when the hold ends) | `server.js`, `client.js`; Roblox `WildPetSpawner`, `FreezeService` | play |
| DR-06 | Ice Ray cubes grow +12% a level for the first 4 levels, then +2% | `config.js` | play |
| DR-07 | The free bridge moved to the far edge (x -68); the ice bridge sits on the gate-to-pen line with a freeze spot on each bank | `config.js`, `scenery.js`; Roblox `Config`, `WorldService` | bridge run |
| DR-08 | Each zone keeps 2 Commons or Uncommons near; Rare and up only spawn in the far half; a small diamond marks the nearest pet | `server.js`, `client.js`; Roblox `WildPetSpawner` | bot + screenshots |
| DR-09, DR-10 | An Index page is the 7 regular pets (the Secret is a bonus slot); after the Forest the goal bar says "Unlock Sunny Beach: coins / 500" | `server.js`, `hud.js` | play |
| DR-11 | No hidden timer on the Super Freeze offer: it goes only when you walk off or zap the pet | `server.js`; Roblox `WildPetSpawner` | suite |
| DR-12 | Rarer banks get a bigger show: more particles, Epic+ banner and light pillar, a longer fanfare | `client.js`, `audio.js` | play |
| DR-13, PT-04 | Signs, boards and landmarks fade when they're between the camera and you | `scenery.js`, `client.js` | camera run |
| DR-14 | Calmer exposure, bluer sky, warmer sun, wind ripples in the snow, smaller zone sign, wild pets 15% bigger with a brighter ring | `client.js`, `scenery.js` | screenshots |
| DR-15, DR-16 | No "+0/s" and no 0 or "-" scores; plainer words ("Normal", "Bigger cubes that last longer", "Run faster") | `hud.js`, `client.js` | play |
| DR-17 | Frosty pets get snowflake sparkles instead of a pale tint | `client.js` | play |
| DR-18 | Leaderboards moved to the screen-right side of the hub | `config.js` | screenshots |
| DR-19, DR-20 | Reduced motion also stills the 3D decoration; the two "!" badges never wiggle together | `client.js`, `index.html` | play |
| DR-21 | Banking in a row climbs in pitch; a different tune in the Forest | `audio.js` | play |
| PT-06 | The paid button sits in its own slot below the free "Zap to refreeze" prompt | `hud.js` | layout check |
| PT-07 | The locked gate always says "Need N more pets" | `client.js` | gate run: passes |
| PT-08 | Prompts keep clear of the banner | `hud.js` | layout check |
| PT-09, PT-10, PT-16 | A popup pauses the player; a double-click doesn't open and shut a menu; Escape closes; toggles are real buttons | `client.js`, `hud.js` | play |
| PT-12 | Gift check is "an earlier day", not "a different day" | `server.js` | suite |
| PT-13, PT-14, PT-15 | Wider key box; popups stay below the top bar with a "more below" hint; phone controls at least 42-44 px; Settings in two columns on short screens | `index.html`, `hud.js` | layout check |
| PT-17 | A "Sunny Beach · coming soon" fence instead of an invisible wall | `scenery.js`, `client.js`, `world.js` | edges run |
| PT-18 | No more toNonIndexed warnings | `scenery.js` | console |

Not changed, and why:
- **DR-02 melt tension**: an owner decision (below). Upgrades make every Meadow and Forest cube safe, so the map alone can't fix it.
- **DR-22 ring route**: two zones don't make a ring; the port's zone layout should.
- **Tablet and PC button sizes** (PT-15 on PC: tiles 86 px, 8% of 1080): [[UI Rules]] set the PC scale to 1.35 on purpose, and a mouse doesn't need thumb-sized buttons, so the UI Rules value stands over the "~10%" in [[QA Rules]] › 5. Touch screens meet 10%.
- **The touch thumbstick drawn over the coins**: it appears where your thumb lands (like Roblox's own); nothing to fix.

## Round 2 checks
- Code auditor's suite: **67 checks, 0 FAIL** in UTC-7 and UTC+14 (round 1: 14 of 65 failed). Five checks were updated to test the new rules (gift after first bank, no hidden offer timer, no 0 shown), and two new ones added.
- Built-in exploit test: 10 checks (2 new: speed hack, object built-in names).
- Layout: phone 844×390, tablet 1024×768 and PC 1920×1080 with no overlaps (thumbstick aside), nothing off screen.
- Bot, 3 seeds × 900 s, 0 errors: first freeze 1.3 s, first bank 2.3 s, first upgrade 13-21 s, Forest opens 35-38 s (≈ 1.5 min kid time), 0 melts.
- **Gamepad:** every action passed in at least one of three runs: move, freeze, bank, open Shop / Index / Settings, buy, switch Index page, every Settings toggle, claim the gift and close it, collect welcome back, open and mock-buy Super Freeze, close with B, a visible selection. One or two checks miss per run, and different ones each time, because the test browser renders at 2-5 fps and sometimes drops a button press. Owner item: try a real controller.
- **Bridges and edges:** every map edge holds; the river blocks; the free bridge crosses; the ice bridge freezes from either bank. When it ends under you, you land on the bank and can walk on (pushed to z 182.5, then walked to z 187.3). The gate says "Need N more pets".
- **Targeted run:** exploit test 10 checks, 0 FAIL; the welcome back shows your best pet; 0 console errors.
- **Bot after its own fixes:**
  - The bot closes popups, uses the ice bridge, chases rare glows (45 studs a tier) and heads to the open Forest.
  - Forest open at 35-45 s (≈ 1.5-1.9 min kid time); Forest reached at 49-58 s.
  - Funnel steps arrive in order. The pen is full (100) by 900 s. 0 melts.

## Owner decisions
Asked on 2026-10-30 (answers below when they come):
1. **Forest gate size.** The Game Plan says 8 pets (§ 4) and Forest at 5-10 min of kid time (§ 17); 8 pets now opens it at about 1.5 min. The pen reached 15 pets at 66-73 s, 20 at 86-95 s, 25 at 106-114 s and 30 at 126-134 s of bot time (× 2.5 for kid time).
2. **Melt tension in the first two zones.** Nothing melts: Ice Ray upgrades make every Meadow and Forest cube safe. The Game Plan's questions (is the run home fun? Super Freeze help or nag?) can't be answered yet.
3. **Earnings while away.** 100% for up to 8 h pays millions of coins a night later on, past every gate.
4. **Port: wild pets shared by the server or personal** (rare rolls, pity).

## Research check (owner request 2026-10-30)
Every note in `Research/` checked against the prototype.
- **[[Research/Game Psychology]]:**
  - Already in the build: sure-to-come rewards with shown odds (2); the goal bar from the first pet (3, 4); silhouettes and a set bonus (5); a 5-year-old core loop with shade routes and pose timing as the teen skill (6).
  - Now in the build: feedback scaled by rarity with rising-pitch streaks (7). Board text that never shames ("not on the board yet", "not in the top 100 yet") (10). The paid button separated from the free one, the Epic FTC dark-pattern lesson (13).
  - Added in round 2: the last step to the Forest is faster (3: one pet short, a pet appears close by), and the welcome back shows your best pet from last time (8, using the Lessons rule that the recap goes on the return).
  - Gaps for the full game, not the prototype:
    - customization and pet naming (1, 9)
    - a pet that follows you (9)
    - other players' wins seen by the server (10, in the Port Plan)
    - one hook each for social and creativity (11: giant cubes, snowballs, cube skins are later layers)
    - a ring route (12)
- **[[Research/Hit Games 2026-10]]:**
  - Already in the build: the verb + reward name, the 3-step chain, upgrades you feel (bigger cubes, faster boots), a shared world moment on a clock that never punishes missing it (the Big Chill), a countable goal on the HUD, a minimal HUD with 3 tiles, and the whole loop shown in the first 30 s.
  - Missing: the clip moment (a melt-and-refreeze save), because nothing melts yet (DR-02).
  - For the full game: a fixed weekly update day (Game Plan 13).
  - Avoid list: nothing in the prototype breaks it. The paid Frozen Crates are the owner's recorded exception (Game Plan 15).
- **[[Research/Game Page Art]]:** applies at pipeline step 9 (page art). The one rule that matters now: the first 3 minutes must match the thumbnail, and the loop shows in the first 30 s.

## Status
- **2026-10-30:** round 1 NO-GO; round 2 fixes in (Halloween repo commit 5772181, artifact version 5); waiting on owner decisions, then the verdict.
