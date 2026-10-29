---
created: 2026-10-29
tags: [game, handoff, prompt]
status: ready to send
---

# Ice Ray for Pets: Build Prompt (for the friend)

The one prompt that builds the whole game. Paste it into Claude Code (or a similar agent) on the builder's machine.

## What to send along
1. **The vault notes** (the whole vault, or at least these): `Games/Ice Ray for Pets/` (Game Plan, Pet Brief, Pet Art Recipe, this note) and `Roblox Setup/` (all the rule notes and Lessons).
2. **The pets folder:** `prototype/ice-ray-for-pets/pets/`. Most important: `frostfox-clay-v1.png` (the style reference every pet must match) and `frostfox-3d-rodin-v1.glb` (the finished 3D Frostfox).
3. The builder needs their own **Figma** (image generation + Weave), **Roblox Studio** and **Obsidian** MCP connections, and optionally **Blender** MCP for mesh cleanup. Paid generations use *their* credits.

## The prompt

```text
You're building the Roblox game "Ice Ray for Pets" (working title) for players aged 5-18: zap wild pets with an ice ray, carry the ice cube home before it melts, and the pet earns coins in your pen. The game is fully designed in my Obsidian vault. Follow the notes; don't redesign anything they already decide. If a note is missing or two notes disagree, ask me instead of guessing.

READ FIRST, in this order:
1. Games/Ice Ray for Pets/Game Plan.md: the whole game (loop, zones, rarity, mutations, money, prototype scope, Roblox port plan).
2. Games/Ice Ray for Pets/Pet Brief.md: which pets the game needs; section 10 is the Snowy Meadow roster with a card and an exact prompt for every pet.
3. Games/Ice Ray for Pets/Pet Art Recipe.md: exactly how a pet picture and its 3D model are made (tool, model, locked clay style prompt, file names, checks, Rodin V2 settings).
4. Roblox Setup/Pet Rules.md, then the other Roblox Setup notes it links (Game Design Rules, UI Rules, World Rules, Animation Rules, Sound Rules, Code Rules, QA Rules, Lessons). They are the quality bar.
The art folder is prototype/ice-ray-for-pets/pets/. frostfox-clay-v1.png is the style reference: every pet must look like it belongs next to it.

HARD RULES
- Money: every paid generation (Figma images, Weave 3D) costs credits. Tell me the count and cost and wait for my OK before each batch. Make one pet first, then the rest of a zone.
- Pets: concepts only from the locked style block + the pet's block (Pet Art Recipe sections 3-4). 3D only from the approved concept image with an image-to-3D model (Weave Rodin V2 is proven). Never build a pet by hand from spheres/cones. Judge every 3D model side by side with its concept.
- Kids: friendly, never scary, original (no other games' or meme characters), no emojis in UI, Robux offers only as the Game Plan's money section allows, with its guardrails.
- Roblox: server-authoritative (the server decides freezes, melt, banking, rolls and purchases), validate every RemoteEvent, save with DataStore pcall + retries + BindToClose, --!strict, task library, Scale-based UI that works on phones.
- Keep the vault up to date: approved pets and prompts into Pet Art Recipe section 6, anything that went wrong into its log and into Roblox Setup/Lessons.md.

WORK IN THIS ORDER. Stop at each [CHECK] and show me before going on:
1. Snowy Meadow pets: generate the 7 concepts that don't have art yet (Pet Brief section 10 has the exact prompts; Frostfox is done). Make a side-by-side line-up. [CHECK]
2. 3D for all 8 Meadow pets with Rodin V2 (Frostfox already has frostfox-3d-rodin-v1.glb). Aim under 8,000 triangles (Rodin's 8K quad option, or decimate in Blender). Show each next to its concept. [CHECK]
3. Design the 8-pet rosters for Pine Forest, Sunny Beach, Desert Dunes and Volcano (Pet Brief section 2 has the themes), as cards in the Pet Brief. [CHECK] Then concepts [CHECK], then 3D [CHECK], one zone at a time.
4. HTML prototype: prototype/ice-ray-for-pets/index.html, three.js 3D, scope exactly as Game Plan section 17, using the real pet models or matching stand-ins. Playable from start to finish in a browser. [CHECK]
5. Port to Roblox Studio following Game Plan section 18 (Config, Theme, PetDefs in ReplicatedStorage/Shared; services in ServerScriptService; effects and HUD on the client). Upload the pet meshes, make glowing parts Neon, rig the pets by family (Pet Rules section 6), add the freeze poses (Pet Brief section 3). [CHECK]
6. QA by playing it in Studio, including a multi-player Start Server test, against Roblox Setup/QA Rules.md. Give me a plain GO or NO-GO with a list of issues.
```

## Status
- **2026-10-29:** written at the owner's request after the pet style (soft clay, `frostfox-clay-v1.png`) and the 3D method (Weave Rodin V2) were proven on Frostfox. The other 7 Meadow pets are intentionally left for the builder (owner: "do not create 7 more pets").
