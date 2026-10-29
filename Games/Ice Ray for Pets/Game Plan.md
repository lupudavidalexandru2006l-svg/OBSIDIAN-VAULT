---
created: 2026-10-29
tags: [game, design, plan, freeze]
status: plan, before prototype
---

# Ice Ray for Pets (working title): Game Plan

The full plan for the freeze-and-run slop. Built from [[Brainstorms/2026-10-29 Unique game ideas]] (rounds 3-4), following [[Roblox Setup/Game Design Rules]], [[Roblox Setup/UI Rules]] and [[Research/Hit Games 2026-10]], except where section 15 says otherwise.

> [!summary] The game in one line
> **Zap a pet with your ice ray and run it home before it melts!** All the systems top slop games have (rarity, mutations, fusing, index, rebirth, a base that earns), but the core action is freeze → carry → race the melt.

---

## 1. Pitch card

| Line | This game |
|---|---|
| **Name** | Working title **Ice Ray for Pets**. Alternatives: Melt Rush, Brr! Catch a Pet. ("Freeze a Brainrot" is taken.) |
| **One sentence** | Zap a pet with your ice ray and run it home before it melts. |
| **The chain** | freeze a pet → carry it home → it earns coins in your pen → better ray and boots → hotter zones with rarer pets |
| **The felt upgrade** | A stronger ray = bigger cubes that melt slower **and** longer ice bridges. Boots = faster runs. Backpack = carry more cubes at once (stacked on your back). |
| **The rare chase** | Mythic and Secret pets in the hottest zones; the Hybrid page of the index; rare poses. |
| **The friend twist** | Giant cubes carry faster with helpers (everyone gets a copy); a snowball hit gives the thrower a copy, the carrier keeps theirs. |
| **The clip moment** | Diving into your pen with a legendary cube one second from melting; a giant cube carried by 4 strangers; a cat frozen mid-sneeze. |
| **The weekly drop** | Every **Saturday**: a new pet family, zone, event or mechanic (section 13). |
| **Three player types** | Social: giant co-op cubes, show-off pen. Mastery: shade routes, pose timing, hot-zone runs. Creativity: hybrid recipes, pen decorating, ice palace. |

## 2. The first minute
1. Spawn next to your pen in **Snowy Meadow**. A green arrow points at a fluffy bunny hopping nearby.
2. Walk up → hold the **Freeze** prompt (1 s) → *fwoosh*, the bunny is in an ice cube on your back. (Reward 1, about 5 s.)
3. The arrow points home. Walk 10 steps, drop it in the pen → the cube cracks, the bunny pops out, dances, and coins start ticking. (About 15 s.)
4. A second and third pet are right there. By about 60-90 s you can afford **Ray Lv 2**, and the next cube is visibly bigger.
5. The goal bar says **"Unlock Pine Forest: 8 pets in your pen"**.

No tutorial text: arrows, glow and the world teach it.

## 3. The core loop (1-3 minutes)
1. **Find** a wild pet (glows in its rarity color, odds shown on the zone sign).
2. **Freeze** it (hold prompt). The pose it's in when the hold finishes is kept (section 6).
3. **Carry** it home. The cube shrinks, drips, cracks. Sun melts it faster, shade slower.
4. **Bank** it in your pen → it earns coins every second, forever.
5. **Upgrade** → go further → hotter zones → rarer pets.

**If a cube melts:** the pet hops out and stands still for a moment, dazed, and one zap re-freezes it (free, always). It isn't yours until it's in your pen, so nothing owned is ever lost. Commons from each zone basically never melt on the main path with the gear needed to enter that zone. Rarer pets are the ones that make the run tense. For Rare and up, a **Super Freeze** button (15 R$) also appears; see section 15.

## 4. The world
The hub (your pen + everyone's pens) sits at the cold north end. Zones get **hotter and further away** going south. The route is a ring: you always run past the next attraction, and the next zone is always in view ahead.

| # | Zone | Heat (melt ×) | Gate (commons only) | Feature |
|---|---|---|---|---|
| 1 | Snowy Meadow | 0.5 | open | learn to freeze |
| 2 | Pine Forest | 0.8 | 8 pets in pen | lots of shade, first ice-bridge river |
| 3 | Sunny Beach | 1.2 | 500 coins | sun patches, shady palm routes, ice slides |
| 4 | Desert Dunes | 1.6 | 25,000 coins | almost no shade, sled hills, oasis shortcuts |
| 5 | Volcano | 2.2 | 1.2M coins | lava you freeze into stepping stones; Lava mutation |

- **Shade**: trees, cliffs, tunnels and drifting cloud shadows melt cubes at ×0.5. Sun patches at ×1.5. Learning the shady routes is the teen skill.
- **Ice bridges**: glowing freezable spots on rivers and lava. Hold Freeze → a bridge for 20 s (longer with ray level). The ray is also how you get around.
- **Sled hills**: jump on your cube and slide down. 2x speed, melts 1.5x faster.
- **Shortcuts**: snowball cannons and penguin taxis (one-way, toward home).
- **Pickups never run out**: wild pets respawn fast, so there's always one within about 3 seconds of walking.
- Depth: snowy mountains and an ice-blue sky in the north, heat haze and a smoking (friendly) volcano far to the south, so the next goal is always visible.

## 5. Pets and rarity
Original, silly creatures, each looking like its name. Each zone has about 6 regular pets + 1 Secret.

| Tier | Spawn odds | Cube life (base) | Coins/sec (Meadow) |
|---|---|---|---|
| Common | 60% | 90 s | 1 |
| Uncommon | 25% | 70 s | 3 |
| Rare | 10% | 50 s | 10 |
| Epic | 4% | 40 s | 30 |
| Legendary | 0.9% | 30 s | 100 |
| Mythic | 0.1% | 25 s | 400 |
| Secret | 1 in 20,000 (zones 4-5) | 20 s | 1,500 |

- Income × **4 per zone** (a Volcano common out-earns a Meadow epic).
- **Cube life = base × ray bonus ÷ heat**, with sun/shade on top.
- **Odds shown on every zone sign**, rolled on the server, with **soft pity** (odds creep up on dry streaks; the shown odds include pity and any active luck potion).
- **Grind check:** in zones 4-5 a run takes about 1 minute, so a 0.1% Mythic takes about 17 hours on average (weeks at 30 min a day). The Secret is a months-long chase, with pity capping the worst case.
- Example Meadow roster: Snowbun (bunny), Pupcicle (puppy), Mittenkit (cat), Waddles (penguin), Frostfox (rare), Yeti Jr (legendary), Aurora Owl (mythic).

## 6. Pose freeze
- Wild pets loop through actions: idle → yawn → jump → dance, with a rare **sneeze**.
- **The pose when your Freeze hold finishes is the pose you keep.** It shows in the pen and earns a bonus.
- Normal ×1, Yawn ×1.2, Jump ×1.2, Dance ×1.5, **Mid-Sneeze ×2** (rare action).
- Timing it right is a skill; little kids just get a fun pose by chance.

## 7. Mutations
| Mutation | How you get it | Bonus |
|---|---|---|
| Golden | fuse 5 of the same pet | ×3 |
| Rainbow | fuse 5 Golden | ×10 |
| Frosty | caught during the Big Chill | ×1.5 |
| Night | caught at night | ×1.5 |
| Lava | 5% of Volcano spawns | ×2 |
| Giant | 2% of spawns, big cube (section 9) | ×3 |

Mutations stack (a Giant Golden Mid-Sneeze Frostfox is the kind of flex teens chase).

## 8. Hybrids (double freeze)
- Two wild pets standing close together (prompt shows **Double Freeze**) → one cube with both inside.
- When it thaws in your pen they **come out fused into a hybrid** (Waddles + Frostfox = Frostwaddle).
- Recipes are **fixed, not random**, so players discover and share them. About 6 hybrids per zone, on their own index page.
- The double cube melts like the rarer of the two pets.

## 9. Giant cubes (co-op, solo possible)
- Giant pets freeze into huge cubes. **Solo you walk at 40% speed**, so it's doable alone, just slow.
- Every helper who grabs it adds +30% speed. **Every helper gets a copy** when it reaches the owner's pen.
- That's the "HELP ME CARRY THIS" moment. It also works on an empty server (solo-first rule).

## 10. Snowballs (light conflict, no loss)
- Throw a snowball at a player carrying a cube → they stumble for half a second and **keep their cube**. The thrower gets a **copy** (Common-Rare) or a coin bonus (Epic and up).
- 30 s cooldown per target, no hits inside the hub, can't target players with much smaller pens. `Config` switch to turn it off.
- **Not in the prototype**; added after the core loop is proven fun.

## 11. Progression systems

**Upgrades** (each step costs ×1.5 the last; income grows slower):

| Upgrade | Effect per level |
|---|---|
| Ice Ray | +20% cube life, +4 s bridge time |
| Boots | +8% run speed |
| Backpack | +1 carry slot (max 5); each extra cube slows you 8% |
| Pen | +5 pet slots |

- **Index**: one page per zone (regular pets × Normal/Golden/Rainbow) + a Hybrid page + a Pose album. **Completing a zone page = +10% coins forever.** Silhouettes show what's missing.
- **Rebirth** (from Desert): resets coins, upgrades and zone unlocks; **keeps pets and the index**. Gives +50% coins forever, a new ray color and the next **ice palace** stage for your pen.
- **Deep freeze vault** (later): store cubes and thaw them during a 2x event.
- **Penguin helpers** (later): penguins carry common cubes home for you (mid-game idle layer).
- **One currency: coins.** No second currency.

## 12. Server moments
- **Day/night cycle** (15 min, 3 of them night): at night cubes melt ×0.6 and pets sleep (instant freeze), but you can't see as far. Sunrise = everyone rushes home.
- **Big Chill** (about every 10 min, announced 30 s before): snow everywhere, **nothing melts for 60 s**, Frosty mutation on everything caught. Can also be bought for the server (section 15).
- **Heat Wave boss** (Saturday event): a giant friendly sun-blob melts the map. The server zaps it together, then carries the giant cube home. Rewards for everyone who helped; solo players get an NPC helper.
- **Social proof**: "Sam caught a MYTHIC Aurora Owl!" banner + a light pillar at their pen. Display names only.
- Missing an event never costs anything.

## 13. Launch content and weekly drops
**Launch:** zones 1-5, about 35 pets + 5 Secrets, pose freeze, mutations, hybrids, giant cubes, index, rebirth, day/night, Big Chill, the full shop (section 15).

| Week (Saturday) | Drop |
|---|---|
| 1 | Heat Wave boss event |
| 2 | Penguin helpers |
| 3 | New zone: Candy Glacier + 7 pets + Candy cube skins |
| 4 | Deep freeze vault + 2x weekend |
| 5 | Ice palace stage 4 + pen decorations |
| 6 | Snowballs (if the playtests say it's kind enough) |

Each drop ships with a new cosmetic set and, where it fits, a new Frozen Crate theme.

## 14. HUD (cap of 5)
1. **Coins**: bottom left.
2. **Menu tiles**: left, centered (Pets, Index, Shop, Rebirth). Red "!" for new.
3. **Goal bar**: top center ("Unlock Sunny Beach: 320/500").
4. Contextual only: event banner (Big Chill, Mythic shout-out, "Sam bought a Big Chill!").

**No melt timer.** The cube itself shows time left (it shrinks, drips, cracks, flashes blue when almost gone). Freezing uses styled prompts on the pets, so there's no HUD action button. The Super Freeze offer is a small button in the world next to the dazed pet, not a HUD element.

## 15. Money (Robux)

> [!warning] Rule change (2026-10-29, the user's decision)
> For this game the user chose to sell **paid luck, paid random pets (Frozen Crates), 2x coins, coin packs and a melt-rescue microtransaction.** That overrides [[Roblox Setup/Game Design Rules]] › 8 and 10 and the project rules ("convenience or cosmetics only", "no paid random rolls", "no surprise pop-ups") **for this game**. The guardrails below keep it inside Roblox policy and stop it from feeling like a trap. The global rules are unchanged unless the user says otherwise.

### Melt rescue: Super Freeze (developer product, 15 R$)
- When a carried cube melts, a **Super Freeze** button appears next to the dazed pet. It refreezes the pet in a deep-blue cube that **never melts until you reach your pen**.
- **Guardrails:** only for **Rare and up**; a small button in the world next to the pet, never a full-screen pop-up; **no countdown** on it; the free re-freeze (one zap) always still works; it goes away when you walk off or zap the pet yourself; at most once per run.
- Also sold up front in the shop as **Super Freeze charges** (1 for 15 R$, 10 for 129 R$), used with a tap when a cube is about to melt.

### Server events (developer products, repeatable)
| Product | Effect | Robux |
|---|---|---|
| Big Chill | nothing melts for 60 s, whole server | 99 |
| Night Time | night for the whole server | 99 |
| Mythic Hour | more rare spawns for everyone, 5 min | 249 |
| Heat Wave boss | summons the boss for the server | 399 |
A server-wide shout-out names the buyer.

### Luck (developer products)
| Product | Effect | Robux |
|---|---|---|
| Luck Potion | 2x rare-spawn luck for you, 15 min | 49 |
| Mega Luck Potion | 3x luck, 15 min | 129 |
| Server Luck | 2x luck for the whole server, 10 min | 299 |
- **The odds on zone signs update live** to include your active potion and pity.
- Luck only raises odds in zones you've unlocked; gates stay reachable with commons only.

### Frozen Crates (paid random pets)
- A crate machine in the hub: pay Robux → a frozen crate thaws into a random pet (short opening show, longer for rarer pets).
- **Odds shown on the machine before buying**, per pet and tier.
- **Hidden where paid random items are restricted:** on the server, check `PolicyService:GetPolicyInfoForPlayerAsync(player).ArePaidRandomItemsRestricted` and don't show the machine at all for that player.
- Crates hold the **same pets you can catch for free**, plus crate-only cosmetic variants. No pet is crate-only.
- The server rolls the result before the show plays (no fake near-misses).

| Crate | Robux |
|---|---|
| Frozen Crate | 99 |
| 3 Frozen Crates | 249 |
| Glacier Crate (better odds) | 399 |

### Coins
- **2x Coins** gamepass (349 R$): double pen income, forever.
- **Coin packs** (developer products), scaled to the player's own income so they stay useful all game: "1 hour of your pen's income" for 99 R$, "5 hours" for 399 R$.

### Cosmetics (the walking billboard)
Cube skins (49-249), ray beam colors and freeze effects (49-199), trails, pet hats, pen and palace themes. The cube on your back is seen by the whole server on every run, so cube skins are the main cosmetic.

### Gamepasses
| Gamepass | Robux |
|---|---|
| 2x Coins | 349 |
| VIP (badge, lounge, gold name, VIP ray) | 249 |
| Auto-collect | 149 |
| Teleport home (zones you've unlocked) | 199 |
| +1 Backpack slot | 199 |
| Extra pen decoration slots | 99 |

### Other
- **Starter pack** (99 R$, one-time): cube skin + ray color + 1 Luck Potion + 3 Super Freezes.
- **Gifting**: every gamepass and cosmetic can be bought for a friend.
- **Private servers**: 100 R$/month.
- **Premium Payouts** from playtime: retention is money, so weekly drops stay the priority.

### Still never
- Pop-ups that cover the screen, countdowns on offers, "last chance" or fake scarcity.
- Hidden or changing odds, fake near-misses, celebrations bigger than the real result.
- Making free play worse to push purchases: melt speeds, spawn rates and gates are tuned for free players first.
- A pet or zone you can only get by paying.
- Every price shows the Robux icon; every buy goes through Roblox's own purchase prompt.

All prices live in `Config.monetization` so they can be tested and changed.

## 16. MVP hooks (from Game Design Rules › 8)
- **Variable reward, sure to come:** every freeze gives a pet; only rarity, pose and mutation are a surprise.
- **Head start:** the goal bar starts with your first pet already counted.
- **Felt upgrade:** bigger cubes, faster boots, longer bridges.
- **Small frequent wins:** a pet banked every loop, rising chimes on streaks.
- **Unfinished collection:** index silhouettes.
- **Welcome back:** "Your pets earned 12,400 coins while you were away" + Collect, stamped at once (no double claim).

## 17. Prototype scope (Stage 1, HTML)
`prototype/ice-ray-for-pets/index.html`, three.js 3D, published as an artifact.

**In:** hub + Meadow + Forest, 8 pets, freeze → carry → melt, shade and sun patches, pose freeze, one ice-bridge river, pen income, Ray / Boots / Backpack upgrades, index page, Big Chill, welcome-back gift, goal bar, odds on the zone sign, a **mock Super Freeze button** (no real money in the prototype) to test where it shows. Test tools: playtest bot (`?bot=1`) and the timer panel (T).

**Out (later):** hybrids, giant cubes, snowballs, rebirth, night, boss, penguins, vault, palace, the rest of the shop.

**Questions the prototype must answer:**
- Is the run home fun, or just walking? (Tune distance, shade and melt.)
- Do little kids ever fail with commons? (They shouldn't.)
- Is pose timing readable on a phone?
- Does the Super Freeze button feel like help or like a nag?
- Grind budget: first reward under 10 s, first upgrade 30-120 s, Forest at about 5-10 min of kid time.

## 18. Roblox port sketch (Stage 2)
| Piece | Where |
|---|---|
| `Config`, `Theme`, `PetDefs` (roster, odds, poses, hybrids) | `ReplicatedStorage/Shared` |
| `WildPetSpawner` (spawn rolls, pity, luck, respawn) | `ServerScriptService` |
| `FreezeService` (prompt validation, pose capture, double freeze) | `ServerScriptService` |
| `CarryService` (melt ticking **on the server**, shade zones, giant carry, Super Freeze) | `ServerScriptService` |
| `PenService` (banking, income, welcome back) | `ServerScriptService` |
| `ShopService`, `IndexService`, `RebirthService`, `EventService` | `ServerScriptService` |
| `MonetizationService` (one `ProcessReceipt`, gamepass checks, crate rolls, PolicyService check) | `ServerScriptService` |
| `DataService` (pcall + retries, save on leave and BindToClose) | `ServerScriptService` |
| Cube melt effects, camera, HUD | `StarterPlayerScripts`, `StarterGui` |

**Security:** the server decides the freeze (distance + cooldown), the pose, the melt time and the bank (must be inside your own pen). The client only plays the effects. All rolls are on the server. Every developer product is granted only inside `ProcessReceipt`, saved before returning `PurchaseGranted`, so a crash never loses a purchase or grants it twice.

## 19. Risks
- **Melt = timer pressure.** Keep commons safe, failure gentle (free instant re-freeze), and no timer on the HUD.
- **Super Freeze can feel like a nag**, or like the game melts things on purpose to sell it. Free players' melt speeds must stay fair; test it in the prototype.
- **Paid crates and luck** bring parent complaints and refund requests, and are blocked in some countries (PolicyService handles that). Odds must always be accurate.
- **Long runs from the Volcano** could feel like walking. Fix with shortcuts, slides, taxis and sled hills; test with the bot.
- **Phone performance** with many cubes, pets and melt effects: cap visible wild pets per zone, simple cube meshes.
- **Name** not settled yet.

## 20. Open questions for the user
- Final name.
- Snowballs at all, or only co-op?
- Pet art direction (round and squishy vs. chunky toy-like).

## Status
- **2026-10-29:** plan written at the user's request after picking freeze-and-run in the brainstorm.
- **2026-10-29:** money section rewritten at the user's request: paid luck, Frozen Crates, 2x coins, coin packs and the 15 R$ Super Freeze added, with guardrails. Next: the HTML prototype (section 17).
- **2026-10-29:** the global rules now allow everything in section 15 (CLAUDE.md, the kids-roblox-game-design skill and [[Roblox Setup/Game Design Rules]] › 10), so section 15 is no longer an exception for this game, just the standard rules applied.
- **2026-10-29:** pet style locked (soft clay) and the 3D method proven on Frostfox (Weave Rodin V2); see [[Games/Ice Ray for Pets/Pet Art Recipe]]. The one-prompt handoff for building the whole game is [[Games/Ice Ray for Pets/Build Prompt]].
