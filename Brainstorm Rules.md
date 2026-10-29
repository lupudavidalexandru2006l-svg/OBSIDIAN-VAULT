---
created: 2026-10-29
tags: [roblox, brainstorm, game-design, rules]
status: draft, not used yet
---

# Brainstorm Rules

How we find a new game (or a big feature) before anything is designed. The output is **three short pitches the user picks from**; the winner then gets the full pitch card in [[Game Design Rules]] › 1. Related: [[Research/Hit Games 2026-10]], [[Research/Game Psychology]], [[Lessons]], [[Home]].

> [!summary] The short version
> **Research what's blowing up right now, borrow patterns (never whole games), go wide, cut hard, score honestly, pitch three.** Every idea is a verb + a reward a 7-year-old gets and a 15-year-old thinks is cool, with one fresh twist that makes it ours.

## 1. Refresh the research
Hits fade within weeks, so research older than about a month is stale.
- **Look at:** the top and rising Roblox games right now (live players, the emerging charts), and **small, cheap Steam games that suddenly went viral** (simple, odd, very shareable).
- **Skip:** big AAA and competitive games (CS2 and the like). They have nothing to teach our games.
- **For each game write down:** what it is, the core loop, **the hook that made it spread**, and what fits kids 5-18 (borrow / adapt / avoid). Numbers only with a source, marked approx.
- **Save it** as a new note `Research/Hit Games YYYY-MM` (same layout as [[Research/Hit Games 2026-10]]): games, Patterns, Avoid, Sources. Keep the old ones; the trend over time is useful.
- A research subagent is fine for this step.

## 2. Go wide
Write **10-15 ideas**, each as one line: **Name (verb + reward) — one sentence.** No details yet. Ways to get ideas:
- **Pattern + twist:** a pattern from the research + one fresh twist (e.g. the egg → pet → zone chain + "pets carry you across a river").
- **Theme swap:** a hit whose theme we can't use, with the loop kept and the theme made kid-safe (a drug-dealing business sim → a potion or smoothie shop; a horror co-op → carrying a giant cake home).
- **Steam co-op → Roblox:** a funny co-op game from Steam rebuilt as short Roblox rounds with roles.
- **One verb:** pick a fun physical action (bounce, dig, paint, roll, fly) + "for Eggs / Pets / Treasure", the current naming meta.
- **One player type:** an idea aimed at social, mastery or creativity players first.

## 3. Cut hard
Drop an idea at once if it hits any of these:
- Anything in [[Game Design Rules]] › 11 Never, or the Avoid list in the research (real loss, gambling, crime, horror, weapons, pay-to-win, punishing timers, open text or voice).
- **A clone.** It must not be a remake of one specific existing game with a new name or skin. Borrow a *pattern* that several games share, then add a twist that is ours. Test: if you describe it to someone, do they say "oh, that's just [game]"? Then cut it or change it.
- It needs more than one short sentence to explain to a child.
- It needs a system we can't build well yet (open trading, big combat, physics-heavy multiplayer) for its *core* loop.

Write down **why** each cut idea was cut. Good ideas come back later.

## 4. Score what's left
Score each idea **1-3** on each line (3 = strong). Be honest; a 2 is fine.

| Line | Question |
|---|---|
| **Kid clear** | Can a 7-year-old say the 3-step chain out loud? |
| **Teen cool** | Would a 15-year-old play it without feeling babyish? |
| **Felt upgrade** | Does the reward change how you move or what you reach? |
| **Clip moment** | Is there a 10-second moment worth recording? |
| **Friend twist** | Is playing near others better, with nobody losing anything? |
| **Rare chase** | Is there a weeks-long thing to chase? |
| **Weekly drops** | Can we add something new every week for months? |
| **Trend fit** | Does it ride something rising now (cite the research)? |
| **Buildable** | Can the core loop be a playable prototype quickly, reusing the starter kit? |

Total out of 27. The top three go to the pitch, but **a 1 on Kid clear or Teen cool is a cut**, whatever the total.

## 5. Pitch three
For each of the top three, a short pitch (half a pitch card):
- **Name** and **one sentence**
- **The chain** (3 steps)
- **The felt upgrade** and **the clip moment**
- **The fresh twist** (what makes it ours, not a clone)
- **Why now:** one line citing the research ("bike / ride + egg games rising in Oct 2026")
- **Score** and the biggest risk

Show them side by side. The user picks one (or mixes two). Then fill the full pitch card in [[Game Design Rules]] › 1 and start the prototype.

## 6. Save the brainstorm
Save every session as `Brainstorms/YYYY-MM-DD <topic>.md`: the long list, the cut ideas with reasons, the scores, the three pitches, and which one the user picked and why. What we learn about picking ideas goes into [[Lessons]].

## For a feature (not a whole game)
Same steps, smaller: 5-8 ideas, and two extra cuts:
- It must fit the game's existing chain (it makes the loop better, it doesn't start a second loop).
- It adds **at most one** HUD item, and only if the cap of 5 allows it ([[UI Rules]]).

## Template
```markdown
# Brainstorm YYYY-MM-DD <topic>
Research used: [[Research/Hit Games YYYY-MM]]

## Long list
1. Name — one sentence
...

## Cut
- Name: why

## Scores
| Idea | Kid | Teen | Upgrade | Clip | Friend | Chase | Weekly | Trend | Build | Total |
|---|---|---|---|---|---|---|---|---|---|---|

## Top 3 pitches
### Name
- One sentence:
- Chain:
- Felt upgrade / clip moment:
- Fresh twist:
- Why now:
- Score / biggest risk:

## Picked
Which one, and why.
```

## Status
- **2026-10-29:** first draft at the user's request. Built from the user's research rule (top Roblox games + small viral Steam hits, skip AAA, save in Research, cite it), the pitch card in [[Game Design Rules]], and the Patterns and Avoid lists in [[Research/Hit Games 2026-10]]. Not used yet: the first real brainstorm will test it.
