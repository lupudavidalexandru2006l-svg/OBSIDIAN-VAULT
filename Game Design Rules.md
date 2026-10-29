---
created: 2026-10-29
tags: [roblox, game-design, rules]
status: draft, tested once (Bounce for Eggs, bot playtest)
---

# Game Design Rules

The rules every game's design follows before any code is written. They merge the kids' design skill, the project rules, what hit games do right now ([[Research/Hit Games 2026-10]]) and the psychology research ([[Research/Game Psychology]]). Related: [[UI Rules]], [[Game Page Art]], [[Lessons]].

> [!summary] The short version
> **Easy to learn, long to master.** One verb, one reward, a 3-step chain a 7-year-old can say out loud. A reward in 10 seconds, an upgrade in 30-120 seconds, a rare chase that takes weeks. Every upgrade is *felt*, every win is *celebrated*, nobody ever *loses* what they earned, and luck (earned or bought) only ever makes you *faster*, never *able*.

## 1. The pitch card (fill this in first)
No game starts until this card is filled in and every line passes its test.

| Line | Test | Example |
|---|---|---|
| **Name** | A verb + a reward. The title is the pitch. | "Bounce for Eggs" |
| **One sentence** | A 7-year-old understands it. If not, simplify. | "Bounce higher to grab eggs and hatch pets." |
| **The chain** | 3 steps, said out loud: get → it helps you → reach better stuff | coins → eggs give pets → pets make you bounce to higher islands with rarer eggs |
| **The felt upgrade** | The reward changes how you move or what you reach, not just a number | each pet adds bounce; the pad launches you to the next island |
| **The rare chase** | One thing that takes weeks | a 1-in-1000 Mythic pet |
| **The friend twist** | Playing near others is better, nobody loses anything | bounce on a friend's head for a bonus jump |
| **The clip moment** | A 10-second moment worth recording | the big launch arc onto the next island |
| **The weekly drop** | What changes every week, on a fixed day | a new egg every Saturday |
| **Three player types** | One hook each for social, mastery and creativity players | friends' bounce race / index + hard sky path / decorate your cloud |

## 2. The first minute
- **Goal shown, not told:** arrows, glow and the world teach. No tutorial text. A green arrow points at the next step (coin → egg → pad).
- **First reward within 10 seconds.**
- **First upgrade in 30-120 seconds of kid time.** Not faster: in the test a 5-second upgrade had no build-up and the whole game was over in 20 seconds.
- **Always a visible next thing:** one progress bar toward one named goal (it counts toward the HUD cap of 5 in [[UI Rules]]).
- **The thumbnail, title and first 30 seconds show the whole loop.** If a player has to discover the point, they leave.

## 3. The grind budget
Write the budget down, then set `Config` numbers to hit it. Never finished in one day.

| Goal | Target kid playtime |
|---|---|
| First reward | under 10 s |
| First upgrade | 30-120 s |
| Early tier complete | 30-60 min |
| Mid game | several days of casual play |
| Rarest items | weeks |

- **Three goals at once:** a short one (next upgrade), a medium one (next zone), a long one (fill the index / the Mythic).
- **Costs grow 1.3-1.6x per step, income grows slower,** so later goals take longer without feeling stuck.
- **Gates never need luck.** Every zone gate is reachable with **commons only** (in the test: 3 commons from the zone before). Rare drops make you faster, never able. Duplicates count toward power. (In the test, a gate that needed a 9% drop took 13 hatches.)
- **Keep the world full; pace with prices, not scarcity.** Pickups respawn faster than a kid can collect them, so there is always something within 3 seconds. Slow the game down with costs, never with an empty island.
- **Gated zones** open at milestones, each with better rewards and rarer drops.
- **An index book with empty slots.** Kids want to fill them.
- **Loops of 1-3 minutes.** Each loop ends with a reward.
- **Budget for free players.** The grind budget is measured without any purchase. Paid boosts make it shorter; they never decide it.

## 4. Rarity and odds
| Tier | Odds | Feel |
|---|---|---|
| Common | 60% | constant, fills the book |
| Uncommon | 25% | |
| Rare | 10% | |
| Epic | 4% | |
| Legendary | 0.9% | a story to tell |
| Mythic | 0.1% | the long-term chase |

- **Check the math against the budget:** expected time = 1 / odds ÷ rolls per minute. The roll rate is set by the egg price. At 6 rolls/min a 0.1% item takes about 2.8 hours on average, which is **too fast** for a weeks-long chase. Price the top egg so one roll costs about a minute of play: 0.1% then takes about 17 hours on average, several weeks at 30 minutes a day.
- **Soft pity:** odds creep up slowly on dry streaks so no kid is stuck forever. It cuts the worst case; it never replaces the chase. The odds shown include the pity boost.
- **Odds visible in-game** for anything random, right at the egg, **including any active luck boost**.
- **Rolled on the server only.** The show plays the result; it never decides it.
- **Rarity scales the celebration:** commons get a short pop, rare things get the full opening show (beats in the project rules: title card, pocket stage, build-up, burst, reveal). The best moments are the rarest.

## 5. Depth for teens (without menus)
- **Merge-4 to upgrade** (4 normal → shiny, 4 shiny → mega).
- **Visual mutations:** shiny, giant, rainbow. Same item, a rarer look.
- **Skill challenges** that are optional: a hard obby path, a speed run, a hidden zone. Pitch them **slightly above** the player's level (slight overload helps flow).
- **Cool, not babyish:** sleek names and effects for the top tiers ("MYTHIC", neon), not just cute ones.
- **Every collectible looks like its name.** A "Sun Phoenix" that looks like a round cat breaks trust (and the honest-thumbnail rule).

## 6. Social, kid-safe
- **Light conflict, no loss.** Tag, swap, race, "borrow": the grabber gets a bonus *copy*, the owner keeps theirs.
- **Co-op with roles:** 2-4 friends, each with a job; failure is funny and retried at once.
- **Shared world moments on a clock** (a rare egg rain every 15 min) that kids call out to each other. Missing one never hurts.
- **Gifting** over trading. If trading ever comes: fixed values or gift-only with a confirm screen.
- **No free text** outside Roblox's filtered chat.

## 7. Feel
- **Celebrate everything:** sparkles, confetti, bounce, a happy sound on every win.
- **Feedback scales with value** and never lies: no big "win" show for a worthless result.
- **Failure is gentle:** quick respawn near where you were, no lost progress, no timers or countdown pressure. A "not yet" bounce pad bounces you in place and says how much more you need.
- **Numbers that only go up** feel great (+1 Speed). Use it as a layer, not a whole game.

## 8. Engagement psychology (the hooks we use)
Hit games keep players with well-known psychology (the research and sources: [[Research/Game Psychology]]). We use the hooks that make the game **more fun to return to**, and ban the ones that work by **pressure, loss or deception** (the casino side). The line: *would a parent watching over the kid's shoulder feel OK about it?*

**Build the MVP hooks first.** The first prototype has the six MVP hooks and nothing else; the "Later" hooks are layers added once the core loop is fun. Piling every hook into a first build fights the HUD cap and hides whether the core loop works.

### Use these
| Hook | When | Why it works | How we use it |
|---|---|---|---|
| **Variable rewards, sure to come** | MVP | Unpredictable rewards are the strongest pull there is (the slot-machine effect), but rewards that are too unreliable make players feel cheated | **A reward is certain, its size is a surprise:** every egg gives a pet, only how good is random. Always earnable by playing, odds shown. Paid rolls are allowed too (section 10) |
| **Head start + near-complete progress** (endowed progress, goal gradient) | MVP | A card with 2 free stamps was finished by 34% vs 19%; people speed up near a finish line | The goal bar never starts empty (base bounce counts), the nearest goal and how close it is are always shown |
| **The felt upgrade** (competence) | MVP | Feeling better at it is what keeps players playing | Each upgrade changes movement or reach (bounce height, the next island) |
| **Small frequent wins + juice** | MVP | Each win releases a little pleasure; feedback makes it louder | A reward every loop, rising-pitch sounds on pickup streaks, effects that grow with rarity |
| **Unfinished collections** (Zeigarnik effect) | MVP | Open loops stick in the mind | An index book with silhouettes of what's still missing, a set bonus per zone page |
| **Welcome back** (and end on a high) | MVP | People judge an experience by its best moment and its ending; coming back should feel good, not guilty | On rejoin: "your pets found coins while you were away" with a Collect button. Every loop and round ends with a celebration. Roblox can't show UI while a player quits, so the recap goes on the return, never on the exit |
| **Big rare moments** | Later | Peak moments are what people remember and retell | The full opening show for rare items, a server-wide shout-out |
| **Social proof** | Later | Seeing others win makes the chase feel real | "Sam hatched a LEGENDARY!" banner (display names only, no free text) |
| **Daily gift with a streak that pauses** | Later | A streak motivates; losing it feels bad | A daily gift that **grows** with the streak; missing a day pauses it, it never drops to zero |
| **Choice and ownership** (autonomy, endowment / IKEA effect) | Later | People value what is theirs and what they chose | Pick which zone or pet; name your pet, it follows you; decorate a base |
| **Something new each week** | Later | Novelty brings players back | The fixed weekly drop (section 9) |
| **Fair luck** | Later | Fair games feel worth playing | Soft pity; bad luck slowly gets better |
| **"One more round"** | Always | Short loops make stopping and going on equally easy | 1-3 minute loops, each with a reward and a visible next goal |
| **A hook for each player type** | Pitch | Players split into social, mastery and creativity motivations | The "three player types" line on the pitch card |

### The world: casino floor → theme park
How casinos keep people inside for hours, and the version we build. Theme parks (Disney, Legoland) use the same playbook with families, so we copy them, not the casino's darkest parts. A University of Guelph study found people said they'd stay longer and feel better in open, comfortable "playground" casinos with music than in packed maze layouts.

| Casino trick | Why it keeps people in | Our version |
|---|---|---|
| **Maze layout** (no straight line to the exit; every path passes more machines) | You keep walking past the next temptation | **The loop route passes the next attraction.** Spawn → coins → egg → pad is a ring, and the next island is always in view ahead (the camera looks toward it). No dead ends, no empty corridors. |
| **The next machine is always 3 steps away** | Never a moment with nothing to do | **Something to do within 3 seconds of walking** anywhere: a pickup, a pet, a button, a friend. Pickups respawn faster than they're collected. |
| **Comfortable "playground" spaces** (high ceilings, warm light, soft seats) | People stay longer where they feel good | **Bright, open, cosy hub** with warm light, music, hangout spots (benches, a fountain, a stage) where kids sit with friends and show off pets. |
| **Never-ending sound** (machines chime, wins ring out across the floor) | The room always sounds like someone is winning | **A living soundscape:** gentle music that never stops, and other players' rare hatches are heard and seen nearby (a chime + light pillar). |
| **Blinking lights pull you to machines** | The eye goes to light and motion | **Interactive things glow and bob;** the next goal is the brightest, most animated thing in view. Scenery stays calm. |
| **Free drinks and comps** | A gift makes you feel looked after and stay longer | **Surprise gifts while you play:** a lucky golden coin that spawns now and then, a free gift box for playtime. Playtime progress **carries over between sessions**, so leaving never loses it. Always free, never a sales pitch. |
| **Loyalty card / player level** | A number that grows the longer you stay | **A player level that only rises,** unlocking cosmetic titles and trails at milestones. |
| **No waiting, instant replay** (the "machine zone": play flows without breaks) | Any gap is a moment to leave | **No friction:** instant respawn, no loading screens between zones, auto-collect nearby coins, hatching where you already are (no long walks to a sell pad). |
| **Jackpot sirens everyone sees** | Other people's wins make yours feel close | Server-wide shout-out + a light pillar at the lucky player (same as "Social proof" above). |

**We do NOT copy:**
- **Hiding the time** (no clocks, no windows) to make people lose track. We don't add a clock to the HUD (it isn't needed), but we never work against a kid noticing time; a gentle "great session! take a break?" note after long play is allowed and nice.
- **Hiding the exit:** no "are you sure? you'll lose your bonus" when leaving, no rewards that are lost if you leave.
- **Losses disguised as wins:** a big celebration for a result worth less than what you spent. Celebrations always match the real value.
- **Chips instead of money** to blur real cost. In-game coins are fine (they aren't real money); anything in Robux always shows the Robux price.
- **Designing the "zone" so people can't stop.** Loops end cleanly so stopping is always easy; kids should leave happy and want to come back, not leave drained.

### Never use these (casino-grade tricks)
- **Fake near-misses:** a reel that "just missed" the Mythic, or an animation that teases a better result than the one rolled.
- **Hidden, misleading or changing odds,** including luck boosts that aren't shown in the odds.
- **Paid random items without the safeguards in section 10** (odds before buying, server roll, PolicyService region check).
- **Loss aversion:** streaks that reset to zero, pets that run away, items that rot or expire, "you'll lose your progress".
- **Pressure on purchases:** countdowns, "last chance", fake scarcity, "only 3 left", full-screen pop-ups.
- **Hidden real cost:** confusing currency bundles so the Robux price is hard to see.
- **Confusing buy buttons** that cause accidental purchases.
- **Energy or wait walls** you can skip by paying.
- **Guilt:** "your pet is sad you left", nag messages.
- **Sunk-cost traps:** offers where paying is the only way out. An in-the-moment rescue (like a Super Freeze) is fine only when the free way out still works.
- **Making free play worse** to push a purchase (slower drops, harsher timers, emptier zones).

Why we draw the line here: our players are 5-18 and most of them can't spot these tricks yet. In 2022 Epic Games agreed to pay $520M to the FTC, $245M of it in refunds for dark patterns (confusing buttons, accidental purchases, blocked refunds). Roblox can take a game down or limit who can play it, and parents who feel tricked uninstall it. Honest monetization keeps players for weeks; tricks get a game banned.

## 9. Live updates
- **A fixed weekly update day** (hit games crash within weeks without one). Plan the first 4 drops before launch.
- Each drop = one new thing (pet, zone, event) + swap thumbnail slot 6 ([[Game Page Art]]).
- Events reward showing up; they never punish missing.

## 10. Money (Robux)
Changed 2026-10-29 at the user's request: paid luck, paid random items, coin boosts and small in-the-moment rescues are now allowed, with the guardrails below.

**Allowed to sell**
- **Cosmetics:** skins, trails, effects, base themes, pet hats. The ones other players see during play sell best.
- **Convenience gamepasses:** auto-collect, teleport home, VIP, extra slots.
- **Speed-ups:** 2x coins, coin packs (sized to the player's own income), luck potions (personal or server-wide).
- **Paid random items** (crates, eggs) that hold the same items you can get for free, plus paid-only cosmetic variants.
- **Server-wide events** a player buys for everyone, with a shout-out.
- **In-the-moment rescues:** a small, cheap offer at the moment it helps (e.g. 15 R$ to Super Freeze a melting pet).
- Starter packs, gifting to friends, private servers.

**Guardrails**
- The whole game is fun and completable for free. **No pet, item or zone is only for Robux** (paid-only cosmetic variants are fine). Zone gates stay reachable with commons only.
- **Paid random items:** odds shown before buying, rolled on the server before the show plays, no fake near-misses, and hidden for players where `PolicyService:GetPolicyInfoForPlayerAsync(player).ArePaidRandomItemsRestricted` is true.
- **Luck boosts:** the odds shown in-game update to include them.
- **In-the-moment offers:** a small button in the world or a side panel, never a full-screen pop-up, never a countdown, and the free way out always still works.
- Clearly labeled with the Robux icon, always through Roblox's purchase prompt. Never "last chance", fake scarcity or countdowns on offers.
- Developer products are granted only in `ProcessReceipt`, saved before returning `PurchaseGranted`.
- Free players' odds, speeds and gates are tuned first, then paid boosts on top.

## 11. Never
Real loss (theft, losing items), casino games and betting, crime or scams as the goal, horror or being hunted, weapons and killing, pay-to-protect, content only available for Robux, punishing FOMO timers, open voice or free text, pure clones (borrow the pattern, add one fresh twist), and the tricks in section 8 › Never. Details in [[Research/Hit Games 2026-10]] › Avoid.

## 12. Testing a prototype
Every prototype ships with two test tools, so the rules above are measured, not guessed:
- **A playtest bot** (`?bot=1`) that plays like a focused kid: nearest pickup → buy when affordable → next zone when allowed. It runs at up to 5x speed and reports **game time**.
- **A timer panel** (press T): first coin, first hatch, first upgrade, each zone reached, hatches, power.
- **Kid time ≈ bot time × 2.5** (an estimate until real kids play it). Check every row of the grind budget against it.
- **Run the bot 3+ times**, because luck changes the times. A gate whose time swings wildly needs luck: fix it (section 3).
- **The bot never buys anything**, so the budget it measures is the free player's.
- **Test rejoin twice in a row fast:** a welcome-back or daily gift must not pay out twice.
- **Reset must really wipe:** turn off save-on-leave while wiping, or the old save comes back.
- In the browser pane, **bring the tab to the front** before timing or screenshots: a hidden tab pauses the game.

## Checklist before porting
- [ ] Pitch card filled in, every line passes its test
- [ ] First reward ≤ 10 s, first upgrade 30-120 s of kid time (timer panel, bot × 2.5)
- [ ] Grind budget written down and the `Config` numbers match it (free player)
- [ ] Every gate reachable with commons only; bot runs agree within a minute
- [ ] Pickups never run out (something within 3 s everywhere)
- [ ] Every odd and cost in `Config`, rolled on the server, odds shown (pity and boosts included)
- [ ] Rarest item's expected time is weeks, not hours (price the egg so a roll ≈ 1 min of play)
- [ ] A day-1 player still has short, medium and long goals left
- [ ] The six MVP hooks from section 8 are in; nothing from its "Never" list
- [ ] Every paid item follows the section 10 guardrails (odds, PolicyService, no pop-ups or countdowns, free way out)
- [ ] The hub is a ring with the next attraction in view, no dead ends
- [ ] Welcome-back gift on rejoin, stamped at once (no double claim)
- [ ] Every collectible looks like its name
- [ ] The first 4 weekly drops are planned
- [ ] Nothing from section 11

## Status
- **2026-10-29:** first draft, then engagement psychology, "casino floor → theme park" and the hooks from [[Research/Game Psychology]], all at the user's request.
- **2026-10-29, review + first test:** reviewed for contradictions (leave recap impossible in Roblox → moved to rejoin; rarity math vs "weeks"; playtime gift vs "no reward for staying"; too many hooks → MVP set; daily gift and streak merged). Then tested with the **Bounce for Eggs** prototype (`prototype/bounce-for-eggs/`) and a playtest bot: whole game done in 20 s, a luck-gated zone, an empty island, a double-claim exploit. All fixed here; details in [[Lessons]]. **Not yet played by a real kid.**
- **2026-10-29, money rules changed at the user's request:** paid luck, paid random items (with odds + PolicyService), 2x coins, coin packs, server events and in-the-moment rescues are now allowed (section 10). The project CLAUDE.md and the kids-roblox-game-design skill were changed to match.

## Added 2026-10-29 (Boo Town look back)
- **One currency.** Boo Town had Candy, Spook Points, Gold and Prize Tickets, and kids couldn't tell them apart. Robux is the only other money, and it's only in the shop.
- **A theme that lasts all year.** No game built on one holiday: seasonal games drop the day after. Seasons are overlays (look, music, one event) on top of the rules.
- **Solo first.** Every boss, gate and goal is doable by one young player alone; friends make it faster or funnier, never possible. Features that need a crowd work on a near-empty server (NPC stand-ins).
- **Losing keeps progress.** A lost fight restarts the current step, not the whole fight.
- Details in [[Lessons]] › Boo Town look back.
