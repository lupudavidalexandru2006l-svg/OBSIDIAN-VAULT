---
created: 2026-10-29
tags: [roblox, rules, qa]
---

# QA Rules

Nothing is done until QA says **GO**. QA plays the game: reading the code is not enough. These rules come from the project rules and from Boo Town's three QA rounds (14, 16 and 21 Oct 2026, see [[Lessons]]).

## 1. When QA runs
- **Prototype QA** before porting ([[Home]] › pipeline step 5): play it in the browser from start to finish, with the playtest bot and timer panel ([[Game Design Rules]] › 12).
- **Studio QA** after porting (step 8): solo play, then a multi-player "Start Server" test.
- **No new feature layer before the last QA said GO.** Boo Town kept adding systems (a whole combat layer, contest, rebirth, Fresh Houses, Gold pets) while the last NO-GO list was still open, and the final QA found the combat layer was never logged.

## 2. Three reviewers, one verdict
For a big QA, split the work in three (as subagents) and merge the findings:
1. **Play-tester:** plays every path with key presses, screenshots each problem, writes repro steps.
2. **Code auditor:** remotes, saving, cleanup, errors in the console. Runs an exploit script that sends fake and spammed remote calls (expect 0 FAIL).
3. **Design reviewer (kid lens):** fun, clarity, grind, odds, safety, compared against the rulebook.

Each finding gets an id (PT-01, CA-01, DR-01) so fixes can be tracked.

## 3. Kid lens
- Would a **7-year-old who can't read much** know what to do next without text? Would they get stuck, scared or frustrated?
- Would a **15-year-old** find it cool, not babyish?
- Flag: anything too hard solo, too fast, too wordy, threatening words ("I will SQUASH you!"), minus numbers or zeros shown as a result, a reward card showing what you *didn't* get.
- **Symbols check:** look at every emblem, rune circle, sign and pattern. No symbols with religious, political or hate meanings (Boo Town's coffin show used a six-pointed star; use a hexagon or a plain ring with tick marks).
- **Failure is gentle:** losing never resets progress you already made (Boo Town's bosses reset to full health after losing your hearts).

## 4. Break it
- [ ] Dead ends, stuck states, soft-locks (spawned behind a barrier, "guarded" with no hint what to do)
- [ ] Falling out of the map
- [ ] Spam-tapping every button and prompt
- [ ] Leaving mid-action (mid-show, mid-fight, mid-buy) and rejoining: nothing lost, nothing paid twice
- [ ] Rejoin twice in a row fast (stale saves, double claims)
- [ ] UI left on screen from another mode (a door sign stayed through a whole boss run)
- [ ] Camera blocked by big props or bosses
- [ ] Slow phone / Low graphics setting

## 5. Every input, every device
- [ ] Every action works on **touch, gamepad and keyboard**. A key-only action (Boo Town's emotes: G key only) is a NO-GO.
- [ ] Phone landscape 844×390, tablet 1024×768, PC 1920×1080: nothing overlaps, nothing under the Roblox top bar, buttons at least ~10% of the short side ([[UI Rules]]).

## 6. Security
- [ ] Every remote: types checked, can-do-it-now checked (distance, cooldown, ownership), rate-limited, result decided on the server ([[Code Rules]] › 6).
- [ ] The server uses its own tracked position, never the position the client claims.
- [ ] Player text shown to others goes through `TextService`.

## 7. Social features
- [ ] Tested with **2+ real players** in Start Server. Boo Town never ran one, so every social feature stayed "CAN'T TELL".
- [ ] Works with a small crowd: a feature that needs 3+ players also works (or has NPC stand-ins) on a nearly empty server.

## 8. Test setup in Studio
- Tests use their own **QA save key**, never the live store or a real player's save. Two Studio sessions on one key overwrite each other.
- Rule test suites (server modules run in the Server datamodel) must be all green after every fix.
- Keep the Studio window visible: a hidden window freezes rendering, so visual checks can't be done.
- Dev commands (grant item, force pity, skip act) make rare paths testable; strip or lock them in live servers.

## 9. The verdict
- A plain **GO** or **NO-GO**.
- A NO-GO lists each issue with: **where** (script / object / position), **how to reproduce**, **how bad** (blocker / should fix / small), and a suggested fix.
- Split out **owner items** (product ids, badge ids, real-phone tests) that a helper can't do, and **owner decisions** (odds, prices) that are questions, not bugs.
- Log each fix (what, where, how checked), then re-run the QA items that touch it.

## Status
- **2026-10-29:** first draft, from the project's QA role and Boo Town's three QA rounds. Not yet used on a new game.
