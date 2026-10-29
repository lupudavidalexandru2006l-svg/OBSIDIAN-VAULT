---
created: 2026-10-29
tags: [research, game-design, psychology]
---

# Game Psychology

The psychology behind why players keep playing, from studies and game-design research, and how we use each idea in a kid-safe Roblox game. The rules that came out of it live in [[Game Design Rules]] › section 8. Related: [[Research/Hit Games 2026-10]], [[Lessons]].

> [!summary] Short version
> Players stay when they **feel good at it** (competence), **feel in control** (autonomy), get **rewards that are sure to come but surprising in size**, are **close to a goal**, and **leave on a high**. Casinos and hit games use the same levers. We use them to make the game fun to come back to; we never use them to pressure, trick or take money.

How to read each entry: **the science** → **how games use it** → **our version** → **the line we don't cross**.

---

## 1. The three needs (Self-Determination Theory)
- **Science:** People are motivated when three needs are met: **competence** (I'm getting better), **autonomy** (I chose this), **relatedness** (people I like are here). A 2023 study of online games found **competence and autonomy** predicted players continuing to play, relatedness did not on its own; "achievability" and "immersion" were the design elements that satisfied players. Customization raised MMO players' motivation.
- **Games:** Clear skill growth, meaningful choices, customization, guilds and friends.
- **Our version:** Every session the kid *feels* better (bigger bounce, faster run); they **choose** which zone, which pet to equip, how to decorate; customization everywhere (pet names, colors, trails). Friends make it nicer, but solo play must stand on its own.
- **Line:** Choices are real, not fake "choose to pay or wait".

## 2. Variable rewards (intermittent reinforcement)
- **Science:** Rewards that come on an unpredictable schedule (variable ratio, like a slot machine) build the most persistent behavior. But Jamie Madigan (psychologist, *Getting Gamers*) points out that when a reward is too **unreliable** (Destiny's loot), the habit loop weakens and players feel cheated.
- **Games:** Loot drops, egg hatches, crits, random events.
- **Our version: "a reward is certain, its size is a surprise."** Every egg gives a pet, every chest gives coins; only *how good* is random. Odds shown, rolled on the server, earned by playing.
- **Line:** Never for Robux. Roblox's policy for paid random items requires showing every outcome and the real odds before purchase (including luck boosts), and blocking them entirely for players in restricted regions (`ArePaidRandomItemsRestricted`). We skip paid randomness completely.

## 3. Goal gradient
- **Science:** People speed up as they near a goal. In a café loyalty study (Kivetz, Urminsky & Zheng, 2006) customers bought coffee **about 20% more often** as they got closer to the free one; a 12-stamp card with 2 free stamps was finished faster than a plain 10-stamp card (median about 10 vs 15 days in summaries).
- **Games:** "3 / 4 collected", XP bars, "almost there".
- **Our version:** Always show the nearest goal and how close it is. Break long goals into short steps so a next step is always near. Make the last step a bit faster, not slower.
- **Line:** No "you're so close, pay to finish" offers.

## 4. Endowed progress
- **Science:** Giving people a head start makes them finish more often. In Nunes & Drèze's car-wash study (2006), cards needing 10 stamps with 2 already filled were completed by **34%** of customers vs **19%** for 8-stamp cards from zero, though both needed 8 washes. Endowed customers also came back sooner.
- **Games:** Tutorials that "complete" the first quest step for you; battle passes that start at tier 1.
- **Our version:** New bars and collection books start partly filled (the first pet is given, the first slot of each zone is free). The tutorial counts as progress.
- **Line:** The head start is real progress, never a fake bar that resets.

## 5. Unfinished business (Zeigarnik effect, collection drive)
- **Science (classic):** Unfinished tasks stick in the mind more than finished ones; people like to complete sets.
- **Games:** Pokédex-style indexes, empty slots, silhouettes of unknown items.
- **Our version:** An index with silhouettes of every pet not yet found, a set bonus for completing a zone's page.
- **Line:** Never items that are only obtainable by paying, so the set is always completable for free.

## 6. Flow
- **Science:** Csikszentmihalyi's flow channel: too hard → frustration, too easy → boredom; the sweet spot keeps people absorbed for hours. Skill-challenge balance is needed but not enough on its own. Research (Baumann, Lürig & Engeser, 2016) found **slight overload** helps flow: a bit harder than comfortable.
- **Games:** Difficulty that ramps, dynamic difficulty, optional challenges.
- **Our version:** Core loop always doable for a 5-year-old; optional skill paths (harder obby, speed run) for teens that sit just above their level. Difficulty ramps by zone, not by punishment.
- **Line:** Flow from fun, never a "zone" built so a kid can't stop (see casino section below). Loops end cleanly.

## 7. Juice (game feel)
- **Science:** "Juice" = generous feedback on every action (Jonasson & Purho's talk *Juice It or Lose It*; Vlambeer's screenshake talk). It's often dismissed as cosmetic, but it changes how the game *feels*. Caution from research: piling on positive-affect stimuli can work against flow, so more is not always better.
- **Games:** Particles, screen shake, squash and stretch, sound pitch rising with combos.
- **Our version:** Every action gets feedback; feedback size scales with value (common = pop, mythic = full show). Rising-pitch sounds on streaks of pickups. Test it: if the effects distract from the next goal, cut them.
- **Line:** Celebrations match the real value: no big "win" show for a worthless result (casinos' "loss disguised as a win").

## 8. Peak-end rule
- **Science:** People judge an experience by its **peak** and its **end**, not its length. In Kahneman's 1993 cold-water study, people preferred a longer trial that ended slightly less painfully. A CHI 2016 study on games found the order of difficulty (peak-end) changed how challenging players remembered a game.
- **Games:** Boss fights, end-of-match summaries, a reward on logout.
- **Our version:** **End sessions on a high.** When a kid leaves (or after a long session), show a short "today you found..." recap with the best moment first, and give the daily gift at the *end* of a loop, not at login only. Every round ends with a celebration.
- **Line:** No guilt at the end ("are you sure? your pet will miss you").

## 9. Ownership (endowment effect)
- **Science (classic):** People value things more once they own them, and more again when they built them (the "IKEA effect").
- **Games:** Housing, pet naming, building.
- **Our version:** Name your pet, it follows you, decorate a base; show the kid's collection in the world.
- **Line:** Never threaten to take owned things away.

## 10. Social proof and status
- **Science (classic):** People follow what others do; seeing others win makes a goal feel reachable.
- **Games:** Server-wide drop announcements, leaderboards, rare cosmetics on display.
- **Our version:** "Sam hatched a LEGENDARY!" banner and light pillar; rare pets visible following their owners; small, friendly leaderboards (this server, this week).
- **Line:** No free text; display names only; no shaming low scores.

## 11. Different players want different things
- **Science:** Quantic Foundry's Gamer Motivation Model (data from hundreds of thousands of gamers) finds 12 motivations in 6 pairs and 3 groups: **Action-Social**, **Mastery-Achievement**, **Immersion-Creativity**.
- **Our version:** Each game gives one hook per group: something to do with friends (Action-Social), something to master and complete (Mastery-Achievement), something to explore or express yourself with (Immersion-Creativity).

## 12. Casino space
- **Science:** A University of Guelph study showed gamblers videos of two casino designs: the **Friedman maze** (low ceilings, games packed in a maze) and the **playground** design (open, comfortable, fantasy). With music, people said they'd **stay longer and feel better** in the playground design; one author told the New Yorker playground gamblers "stay longer, feel better, and bet more". The playground style was popularized by Steve Wynn's designer Roger Thomas. Some "no clocks, no windows" stories are partly myth.
- **Our version:** Covered in [[Game Design Rules]] › "casino floor → theme park": a bright, comfortable hub with music, the loop route passing the next attraction, something to do within 3 seconds, surprise free gifts.

## 13. Where it becomes a dark pattern
- **Fact:** In December 2022 Epic Games agreed to pay **$520M** to the FTC: **$275M** for children's privacy (COPPA) and **$245M** in refunds for "dark patterns" (confusing button layouts that caused accidental purchases, and roadblocks to getting refunds). Refunds have gone to well over a million players since.
- **Our line, in one sentence:** a trick is OK if it makes the game more fun **and** the kid would still feel good about it if a parent explained it to them; it's banned if it works through pressure, loss, confusion or money.

---

## Trick sheet (what goes in every game)
| # | Trick | Where it lives |
|---|---|---|
| 1 | A reward is certain, its size is a surprise | eggs, chests, drops |
| 2 | Bars and books start partly filled | HUD goal bar, index |
| 3 | The next goal is always close and visible | HUD goal bar |
| 4 | Silhouettes of what's still missing | index |
| 5 | Feedback scales with value; rarer = bigger show | effects, opening show |
| 6 | Core loop easy, optional challenges slightly too hard | zones, skill paths |
| 7 | End sessions on a high: "today you found..." recap | leave / long-session moment |
| 8 | Real choices and customization | pets, base, trails |
| 9 | Others' wins are seen and heard | banner, light pillar |
| 10 | One hook each for social, mastery, creativity | pitch card |
| 11 | Playground hub: bright, music, ring route | world layout |

## Sources
- Tyack & Mekler, Self-Determination Theory in HCI games research (CHI 2020): https://acris.aalto.fi/ws/portalfiles/portal/40334523/CHI2020_SDT_in_Games_preprint.pdf
- Competence and autonomy drive online game continuance (Int. J. of Information Management, 2023): https://ira.lib.polyu.edu.hk/handle/10397/108587
- Customization and MMO retention (Cyberpsychology): https://cyberpsychology.eu/article/download/4340/3411
- Game engagement theory (Wikipedia, starting point only): https://en.wikipedia.org/wiki/Game_engagement_theory
- Jamie Madigan, Psychology and Destiny's loot system: https://www.gamedeveloper.com/design/psychology-and-destiny-s-loot-system
- Getting Gamers (Publishers Weekly review): https://www.publishersweekly.com/978-1-4422-3999-9
- Kivetz, Urminsky & Zheng, The Goal-Gradient Hypothesis Resurrected (2006): https://business.columbia.edu/sites/default/files-efs/pubfiles/1200/goalgradient.pdf
- Chicago Booth Review on goal gradient: https://www.chicagobooth.edu/review/going-goal
- Endowed progress (Goal pursuit, Wikipedia): https://en.wikipedia.org/wiki/Goal_pursuit
- Designing Game Feel, a survey (Pichlmair & Johansen): https://arxiv.org/pdf/2011.09201
- Game feel and juice: https://eolt.org/articles/game-feel/
- Flow and skill-challenge balance (PeerJ): https://peerj.com/articles/10520.pdf
- Baumann, Lürig & Engeser, flow and slight overload (2016): https://www.uni-trier.de/fileadmin/fb1/prof/PSY/PGA/unterlagen/BaumannL%C3%BCrigEngeser_Flow_MOEM_2016.pdf
- Positive affect and flow (Cyberpsychology): https://cyberpsychology.eu/article/view/30988
- Gutwin et al., Peak-end effects in games (CHI 2016): https://www.cs.mcgill.ca/~jeromew/data/COMP766/CHI2016/p5608-gutwin.pdf
- Quantic Foundry, Gamer Motivation Model: https://quanticfoundry.com/
- Nick Yee GDC 2019, the 12 motivations: https://gdcvault.com/play/1025742/contactUs
- University of Guelph casino design study: https://www.uoguelph.ca/mediarel/archives/003453.html
- Gizmodo, how casinos use design psychology: https://gizmodo.com/how-casinos-use-design-psychology-to-get-you-to-gambling-1667182023
- Casino.org, Vegas myths (clocks and sunlight): https://www.casino.org/news/vegas-myths-busted-casinos-sunlight-and-clocks-to-trick-gamblers/
- Roblox, Paid random items policy: https://create.roblox.com/docs/production/monetization/paid-random-items
- PBS, Epic Games $520M FTC settlement: https://www.pbs.org/newshour/amp/nation/fortnite-maker-epic-games-to-settle-ftc-case-pay-520-million-in-penalties-and-refunds
- PYMNTS, FTC Epic refunds: https://www.pymnts.com/legal/2024/ftc-begins-sending-refunds-in-epic-games-settlement/

Numbers marked "in summaries" come from secondary write-ups of the papers; check the original paper before quoting them anywhere public.
