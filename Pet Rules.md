---
created: 2026-10-29
tags: [roblox, pets, characters, art, rules]
status: tested on Ice Ray for Pets (2026-10-29), concept style and 3D method proven on one pet
---

# Pet Rules

How we design and build pets (and any collectible creature). **Pets are made first, before the prototype's systems**, because in a collection game the pets *are* the product: they're what kids chase, show off, buy in crates, put in thumbnails and clip. Related: [[Game Design Rules]] › 4-5, [[Animation Rules]] › 4, [[UI Rules]] › Icons, [[Sound Rules]], [[World Rules]] › 6, [[Code Rules]], [[Lessons]], [[Home]]. A game's own roster lives in its folder (e.g. [[Games/Ice Ray for Pets/Pet Brief]]), and its step-by-step art method in a recipe note (e.g. [[Games/Ice Ray for Pets/Pet Art Recipe]]).

> [!summary] The short version
> **Every pet looks like its name, reads as a black silhouette at phone size, belongs to one family, and gets fancier the rarer it is.** Design a whole zone on paper, generate one painted concept per pet from one fixed style prompt, get the owner's OK, then turn each concept into 3D with an **image-to-3D generator**, never by hand. Commons are cute and simple; Mythics and Secrets are the coolest thing in the game.

## 1. Why pets first
- **Kids pick a pet game for its pets.** The systems only matter once the pets are worth having.
- **Everything else depends on them:** the index, the crates (money), the opening shows, the page art, the weekly drops.
- **Pets take the most work** (concept → 3D model → rig → animations → mutations → icon → sound → checks) and the most rounds of the owner's feedback. Starting them first means they're ready when the systems are.
- The prototype can use **simple stand-in shapes** until the real pets are approved, but the stand-ins use the real names, sizes and colors so the swap is clean. Stand-ins are never shown as "the pet".

## 2. The pet card (one per pet)
Fill this in for every pet before any art. Keep it in the game's Pet Brief.

| Field | Test | Example |
|---|---|---|
| **Name** | Says what it is, fun to say, sleek for top tiers | Frostfox |
| **Species / body plan** | One of the rig families (section 6) | quadruped |
| **Zone + tier** | From the game's roster plan | Snowy Meadow, Epic |
| **Main color** | One main color from `Theme`, different from every other pet in its zone | deep teal |
| **Silhouette hook** | The one shape that makes it recognizable as a black shape | tail bigger than its body, ending in a glowing crystal |
| **Personality** | One word | show-off |
| **Signature move** | Matches the name; plays in the reveal and on the happy action | tail swish that leaves a snowflake trail |
| **Game poses** | The game's extra poses (e.g. the freeze poses) | yawn, jump, dance, sneeze |
| **Sound** | A short happy sound + a signature sound | soft yip + wind chime |
| **Size class** | S / M / L (section 4) | M |
| **Mutation notes** | Anything special about how mutations look on it | Golden turns the tail into gold leaf |
| **Hybrid partners** | Which pets it fuses with, if the game has hybrids | Waddles → Frostwaddle |
| **Prompt** | The exact pet block for the concept prompt (section 9) | "The pet: Frostfox, a baby arctic fox..." |

## 3. Design rules
- **Looks like its name.** A "Sun Phoenix" that looks like a round cat breaks trust (Bounce for Eggs taught this). From a distance too.
- **Silhouette test:** fill the concept black. A kid must still tell it apart from every other pet in its zone at **48 px** (index icon) and at **30 studs** in game on a phone.
- **One main color per pet, different from the rest of its zone, deep and saturated.** A zone family shares a theme (materials, accessories), not a color. If the game has a container with a tint (e.g. a light-blue ice cube), no main color may be close to that tint.
- **Chunky toy proportions:** big head (about 45-55% of height), round body, stubby limbs, big readable eyes (simple round black eyes with one white shine dot, no eyelashes), a simple happy face. Shapes read at phone size; tiny details don't.
- **Friendly, never scary:** no fangs or teeth showing, no angry or narrow eyes, no claws out, no weapons, no blood or skulls. Dragons, sharks and monsters are fine if they're clearly cute.
- **Cool, not babyish, at the top:** Legendary, Mythic and Secret pets get sleek names, armor plates, crystals, flames, neon parts, wings or auras, so a 15-year-old wants them too.
- **Original only.** No meme characters (brainrot, Skibidi), no Pokémon, Adopt Me, Pet Simulator or any other game's pets, no brands. Test: describe it to someone; if they say "oh, that's just [character]", redesign it.
- **Every symbol and emblem is checked** ([[QA Rules]] › 3): no stars of David, crosses, crescent moons, swastika-like shapes, gang signs or real flags by accident. Use snowflakes, hearts, gems, leaves, suns instead.

### Rarity ladder (how fancy each tier is)
| Tier | Looks | Motion | Effects |
|---|---|---|---|
| Common | simple shapes, 1-2 colors, the cutest | idle bob | none |
| Uncommon | + one accessory (scarf, hat, flower) | + a little extra bounce | none |
| Rare | + a pattern or material (stripes, fur tufts, shell) | + a personality idle | a soft sparkle now and then |
| Epic | + one glowing part (Neon eyes, gem, crest) | + a signature idle | small glow |
| Legendary | elaborate shape (wings, crown, armor, flames) | full signature idle | aura or particles |
| Mythic | a unique body plan, several neon parts, a trail | floats or poses, unique idle | aura + trail + light motes |
| Secret | the strangest, coolest design in the game, a mystery theme | its own animation set | everything, plus a unique sound |

The rarer it is, the more it should be **visibly** worth it. Nobody should mistake an Epic for a Common.

## 4. A family looks like one family
- **One art style per game, locked after a style test** (section 5 step 2). Same proportions, eye style, finish and light direction for every pet.
- **Light from the top left** in all concepts and icons, like the UI icons.
- **Glowing parts stay smooth and glassy** (crystals, gems, neon) so they stand out against the body's finish. In Roblox they become Neon parts or get a light, because generated textures don't glow.
- **Size classes:** S about 2 studs tall, M about 3, L about 4. Giant mutation = 2.5x. Pets never hide the player.
- **Lay a whole zone out side by side** (the "line-up") before 3D work. Check: different silhouettes, different main colors, the rarity ladder is visible from left to right.

## 5. The pipeline (in order)
1. **Roster plan.** The game's Pet Brief lists every slot: zone, tier, theme. Fill a pet card for each. The owner approves the roster.
2. **Style test (once per game).** One generation showing **the same pet in three styles side by side** (it costs one image and gives a real choice). The owner picks one; that style block is locked in the game's recipe note.
3. **Concept art, one image per pet.** Figma `generate_image`, model `gpt-image-2.5-sunburst`, 1024 × 1024: locked style block + the pet's block (section 9). 3/4 front view on plain white, full body, the silhouette hook visible. **Every generation costs credits, so confirm each batch with the owner first**, and make one pet before the rest of a zone. Download the PNG at once (the link expires after 7 days).
4. **Line-up review.** The zone's concepts side by side on the game's background color. The **owner approves the family** before any 3D work. Redo single pets until they pass section 3.
5. **3D model from the concept image.** An image-to-3D generator, judged side by side against the concept:
   - **Proven:** Figma Weave → **Rodin V2**, about 36 Weave credits, about 2 minutes, a textured GLB that matched the concept closely (Ice Ray for Pets, Frostfox, 2026-10-29). Ask for the 8K-quad or 20K-triangle mesh option.
   - Also possible: other Weave models (Trellis 2, Hunyuan 3D, Meshy), Blender MCP `generate_3d` with a provider switched on.
   - Fallback only: Roblox Studio `generate_mesh` (text only, can't see the concept).
   - **Never:** building the pet by hand from primitives (spheres, cones). It was rejected outright ("looks very shit and nothing like the photo"): it can't reach the concept's detail.
   Rules for every method: **under 8,000 triangles per pet** as the target (20,000 is Roblox's hard cap per mesh; decimate in Blender if needed), colors in a texture so they survive upload, imported FBX comes in 100x too big (scale 0.01).
6. **Rig.** One skeleton per rig family (section 6), with the **same bone names** across the family so animations are shared.
7. **Animations.** The base set (idle, move, happy, signature) per [[Animation Rules]] › 4, plus the game's extra poses. Upload under the game's owner account or group (animations owned by someone else won't play). IDs go in `Config`.
8. **Mutation looks** (section 7), made as material/color/effect swaps on the same model, never new models.
9. **Hybrids** (if the game has them, section 8).
10. **Index icon** for every pet: painted like the UI icons ([[UI Rules]] › Icons), same outline, light and size, made from the approved concept. Silhouette version for "not found yet".
11. **Sounds:** a short happy sound and a signature sound per pet ([[Sound Rules]]). The rarer, the more special.
12. **In-game checks** (section 10), then into `PetDefs`.

## 6. Rig families (share the work)
Every pet uses one of a few skeletons, so one animation set covers many pets.

| Family | Pets | Bones (same names in every pet) |
|---|---|---|
| Quadruped | dogs, cats, foxes, bunnies, bears | Root, Body, Head, LegFL, LegFR, LegBL, LegBR, Tail, EarL, EarR |
| Biped | penguins, yetis, monkeys | Root, Body, Head, ArmL, ArmR, LegL, LegR, (Tail) |
| Bird / flyer | owls, phoenixes, bats, dragons | Root, Body, Head, WingL, WingR, Tail, (LegL, LegR) |
| Blob | slimes, jellies, ghosts, sun-blobs | Root, Body, Top (squash and stretch only) |
| Swimmer | fish, seals, whales | Root, Body, Head, FinL, FinR, Tail |

Unusual pets (Mythic, Secret) may get their own rig and animations; that's what makes them special.

## 7. Mutations (same model, new look)
| Mutation | Look |
|---|---|
| Golden | shiny gold metal material, a few sparkles |
| Rainbow | slowly cycling rainbow colors, sparkle trail |
| Shiny / Crystal | lighter, glassy, with a glint |
| Frosty | ice crystals and frost on the head and back, a cold mist |
| Night | deep blue with star speckles that glow |
| Lava | dark rock with glowing orange cracks |
| Giant | 2.5x scale, deeper voice |

- Mutations **stack**, so each one changes a different thing (material vs. overlay vs. scale vs. effect) and they never fight.
- A mutation is visible at 30 studs on a phone, or it isn't worth having.

## 8. Hybrids
- A hybrid takes the **head and silhouette hook of one parent** and the **body, main color and material of the other**, so both parents are recognizable.
- Both parents must share a rig family, or the hybrid uses the body parent's rig.
- The hybrid's name mixes both names (Waddles + Frostfox = Frostwaddle).
- A hybrid is designed and approved like any pet (pet card, concept, line-up).

## 9. The concept prompt
Every pet prompt = **the game's locked style block** + **the pet block**, nothing else, so the family stays consistent.

- **Style block:** lives in the game's recipe note (Ice Ray for Pets uses style B, soft clay toy: [[Games/Ice Ray for Pets/Pet Art Recipe]] › 3). It always includes: chunky toy proportions, simple round black eyes with one white shine dot and no eyelashes, small happy smile with no teeth, a **deep saturated** main color, full body 3/4 front view, plain white background, no text, frame, shadow or other objects.
- **Pet block:** "The pet: [name], a baby [species]. [Main color] with [accent colors]. [Silhouette hook]. [Rarity extras from the ladder in section 3]."
- What the model gets wrong if you don't say it: pale colors (say "deep, rich, saturated"), anime eyelashes (say "no eyelashes"), realistic fur strands (name the finish you want, e.g. "chunky sculpted fur clumps").
- Check each result for AI drift that breaks the family (a different eye style, a realistic texture, extra limbs) and redo those by changing only the pet block.
- Keep every concept in the game's art folder as `<pet-name>-v<N>.png`; never overwrite an old version.

## 10. In-game checks (every pet)
- [ ] Recognizable at 30 studs on a phone, and as a 48 px icon
- [ ] Looks like its name; different silhouette and main color from its zone mates
- [ ] Reads inside the game's container (cube, egg, crate) and through any effects
- [ ] Looks right in a crowded pen or base with 20+ pets
- [ ] Idle, move, happy, signature and the game's poses all play in a live server
- [ ] Every mutation shows clearly and they stack without fighting
- [ ] Under 8,000 triangles; frame rate is fine with 30 on screen on a phone
- [ ] The 3D model still looks like its concept side by side
- [ ] Friendly, original, symbols checked
- [ ] Sound plays, not too loud, not annoying on repeat

## 11. From art to code
Every pet is one entry in `PetDefs` (`ReplicatedStorage/Shared`), so nothing about a pet is hard-coded:

```lua
--!strict
export type PetDef = {
	key: string,          -- "frostfox"
	name: string,         -- "Frostfox"
	zone: number,
	tier: "Common" | "Uncommon" | "Rare" | "Epic" | "Legendary" | "Mythic" | "Secret",
	rig: "Quadruped" | "Biped" | "Bird" | "Blob" | "Swimmer" | "Custom",
	size: "S" | "M" | "L",
	model: string,        -- name of the model in ReplicatedStorage/PetModels
	icon: string,         -- rbxassetid://
	color: string,        -- Theme key
	anims: { [string]: string }, -- idle, move, happy, signature, + game poses
	sounds: { happy: string, signature: string },
	income: number,
}
```

## Checklist before a zone's pets are done
- [ ] Every slot in the Pet Brief has a filled pet card with its prompt
- [ ] The owner approved the zone's line-up
- [ ] 3D models made from the concepts (image-to-3D), still look like them, under the triangle budget
- [ ] Shared rigs and animations work for the whole family
- [ ] Mutations and hybrids made and checked
- [ ] Painted index icons + silhouettes, same family as the UI icons
- [ ] Sounds in
- [ ] Every in-game check in section 10 passes
- [ ] `PetDefs` entries filled, nothing hard-coded

## Status
- **2026-10-29:** first draft at the owner's request, so pets are made first and to one standard. Built from [[Animation Rules]] › 4, [[UI Rules]] › Icons, [[Game Design Rules]] › 5 and the Bounce for Eggs lesson that every pet was the same round body.
- **2026-10-29:** rewritten after the first real test (Ice Ray for Pets, Frostfox): style test with three styles in one image (owner picked soft clay), image-to-3D with Weave Rodin V2 proven, hand-built Blender pets rejected. Details in [[Games/Ice Ray for Pets/Pet Art Recipe]] and [[Lessons]].
