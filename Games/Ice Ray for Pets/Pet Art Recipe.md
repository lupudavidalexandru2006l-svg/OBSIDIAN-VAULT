---
created: 2026-10-29
tags: [game, pets, art, recipe, ai-images]
status: in progress, art style locked (B, soft clay toy); 3D method being tested
---

# Ice Ray for Pets: Pet Art Recipe

**How every pet picture in this game is made, step by step, so anyone (or any AI agent) can make the rest of the pets the same way.** Hand this note to whoever builds the game, along with [[Games/Ice Ray for Pets/Pet Brief]] (what pets the game needs), [[Games/Ice Ray for Pets/Game Plan]] (the game) and [[Roblox Setup/Pet Rules]] (the quality bar).

> [!summary] The recipe in one line
> **Fill in a pet card → paste its details into the fixed prompt (style B, soft clay toy) → generate with Figma `generate_image` (model `gpt-image-2.5-sunburst`) → download the PNG at once → check it → save as `<pet-name>-vN.png` → line the zone up side by side → the owner approves → turn it into 3D with an image-to-3D model (section 9).**

---

## 1. Tools and where things live

| What | Value |
|---|---|
| Image tool | Figma MCP `generate_image` |
| Model | `gpt-image-2.5-sunburst` (the painted, detailed look; the cheaper Gemini models are not used) |
| Size | `1024 × 1024` for one pet; `1536 × 1024` for a side-by-side comparison |
| Figma file | **Ice Ray for Pets - Pet Concepts**, `fileKey = EQIseY7rLHymUZQuVPANqQ`, https://www.figma.com/design/EQIseY7rLHymUZQuVPANqQ (team plan `team::1687810435973568154`). This one belongs to the owner. |
| Builder's Figma file | The builder makes their own file with the same name and generates into it. David's: `fileKey = gwLGeHxXfjNYdW8vHst6fU`, https://www.figma.com/design/gwLGeHxXfjNYdW8vHst6fU (team `team::1688893383797864407`), created 2026-10-29. |
| Image files | `C:\Users\n2012\Documents\RobloxKidsGames\prototype\ice-ray-for-pets\pets\` |
| File names | `<pet-name>-v<N>.png`, lower case with dashes, e.g. `frostfox-v3.png`. Style tests: `<pet-name>-style-test-v<N>.png`. Never overwrite an old version. |
| Cost | **Every call uses Figma AI credits.** Ask the owner before each batch. Make one pet first, get an OK on it, then do the rest of the zone. |

## 2. Steps for one pet

1. **Pet card.** Fill in the pet's card in [[Games/Ice Ray for Pets/Pet Brief]] (name, species, tier, main colour, silhouette hook, signature move, size). Fields are in [[Roblox Setup/Pet Rules]] › 2.
2. **Build the prompt.** Take the **style block** (section 3) and add the **pet block** (section 4) with the card's details. Change nothing else, so every pet looks like the same family.
3. **Generate.** Call `generate_image` with `fileKey`, `model = gpt-image-2.5-sunburst`, `width = 1024`, `height = 1024`, the prompt. It places the image in the Figma file and returns `image.url`.
4. **Download at once.** `image.url` **expires after 7 days**. Save it straight away:
   ```bash
   curl -f -L -o "prototype/ice-ray-for-pets/pets/frostfox-v3.png" "<image.url>"
   ```
5. **Check it** against section 5. If it fails, change only the pet block (or add a "no X" line) and make a new version. Don't fix it by changing the style block for one pet.
6. **Line-up.** When a zone's pets are all made, put them side by side in the Figma file on the zone's background colour, Common → Secret from left to right. The owner approves the whole family before any 3D work.
7. **Record it.** Put the approved file name and the exact prompt used in section 6 of this note.

## 3. The style block (fixed for every pet): B, soft clay toy

> [!success] Locked 2026-10-29
> The owner picked **style B** (the middle fox in `frostfox-style-test-v2.png`, cropped as `frostfox-clay-v1.png`). This is the reference picture for the whole game: every new pet must look like it belongs next to it.

Paste this block, word for word, at the start of every pet prompt:

> A cute collectible pet for a kids' video game, made as a soft matte clay figure with chunky sculpted fur clumps in big simple shapes, gentle soft shadows, handmade toy look, soft light from the top left. Chunky toy proportions: big head, round body, stubby legs. Simple large round black eyes with one white shine dot, no eyelashes, small happy smile, no teeth. Deep, rich, saturated main colour (never pale, so it shows through a light-blue ice cube), with white accents. Full body, 3/4 front view, centred, plain white background, no text, no labels, no frame, no ground shadow, no other objects.

Glowing parts (crystals, gems, neon) stay **smooth, glassy and glowing**, so they stand out against the matte clay.

## 4. The pet block (changes per pet)

> The pet: [name], a baby [species]. [Main colour] with [accent colours]. [Silhouette hook: the one big shape that makes it recognisable]. [Rarity extras, from the ladder below].

**Rarity extras** (from [[Roblox Setup/Pet Rules]] › 3, the rarer the fancier):

| Tier | Add to the pet block |
|---|---|
| Common | nothing extra, simplest and cutest |
| Uncommon | one accessory (knit hat, scarf, mittens) |
| Rare | a pattern or material (stripes, drips, shell, tufts) |
| Epic | one glowing part (gem, crystal, glowing tip) with a small soft glow |
| Legendary | an elaborate shape (crown, armour plates, wings) with a soft aura |
| Mythic | a unique body, several glowing neon parts, a trail of light motes, floating |
| Secret | the strangest, coolest design of the zone, everything plus a mystery theme |

**Example (Frostfox, Epic):**
> The pet: Frostfox, a baby arctic fox. Deep saturated teal fur with a white chest and white muzzle. A giant fluffy tail bigger than its body, curling up behind it, the tail tip is a glowing cyan ice crystal. A small glowing gem on its forehead.

## 5. Checks for every picture
- [ ] Same style as `frostfox-clay-v1.png` (matte clay, chunky fur clumps, same eyes, same light). Redo AI drift: eyelashes, realistic fur strands, glossy plastic, a different eye style, extra legs, a second animal.
- [ ] Main colour is **deep and saturated**, different from every other pet in its zone, and not light blue or plain white (it has to show through the ice cube).
- [ ] The silhouette hook is big and clear. Fill it black in your head: could a kid tell it from its zone mates at 48 px?
- [ ] Looks like its name.
- [ ] Friendly: no teeth, no claws, no angry or narrow eyes.
- [ ] Original: not a Pokémon, Adopt Me, Pet Simulator, brainrot/meme or brand character.
- [ ] The tier reads at a glance (an Epic glows, a Common doesn't).
- [ ] Shapes are simple enough to rebuild in 3D (big chunky forms, not thousands of hairs).

## 6. Approved pets
| Pet | Tier | File | Prompt used |
|---|---|---|---|
| Frostfox (style reference) | Epic | `frostfox-clay-v1.png` (cropped from `frostfox-style-test-v2.png`) | style test prompt, middle version; for new pets use sections 3 + 4 |
| Snowbun | Common | `snowbun-v1.png` (approved 2026-10-29); 3D `snowbun-3d-roblox-v1.glb` | section 3 style block + the Snowbun block in [[Games/Ice Ray for Pets/Pet Brief]] › 10, word for word |
| Waddles | Common | `waddles-v1.png` (approved 2026-10-29) | section 3 + Pet Brief › 10 Waddles block |
| Mittenkit | Uncommon | `mittenkit-v1.png` (approved 2026-10-29) | section 3 + Pet Brief › 10 Mittenkit block |
| Pupcicle | Rare | `pupcicle-v1.png` (approved 2026-10-29) | section 3 + Pet Brief › 10 Pupcicle block |
| Blizzard Yeti | Legendary | `blizzard-yeti-v1.png` (approved 2026-10-29); 3D input `blizzard-yeti-3d-input-v1.png` (snowflakes removed) | section 3 + Pet Brief › 10 Blizzard Yeti block |
| Aurora Owl | Mythic | `aurora-owl-v1.png` (approved 2026-10-29); 3D input `aurora-owl-3d-input-v1.png` (motes removed) | section 3 + Pet Brief › 10 Aurora Owl block |
| Snowglobe Drake | Secret | `snowglobe-drake-v1.png` (approved 2026-10-29); 3D input `snowglobe-drake-3d-input-v1.png` (sparkles removed) | section 3 + Pet Brief › 10 Snowglobe Drake block |
| Pine Forest and Sunny Beach | all | see the log (section 7); waiting for the owner's line-up review | section 3 + Pet Brief › 11.1-11.2 blocks (Bloomhorn Stag v2 adds the button-eyes line) |

## 7. Log: what was tried
| Date | File | Result |
|---|---|---|
| 2026-10-29 | `frostfox-v1.png` | **Rejected, "looks strange".** Realistic fur strands, anime eyes with eyelashes, colour came out pale sky-blue instead of deep teal (would vanish in the ice cube). Prompt asked for "satin vinyl" but the model ignored it and made fluffy fur. |
| 2026-10-29 | `frostfox-style-test-v2.png` | Three styles in one image (A glossy vinyl, B soft clay, C painted with outline). One generation gives a style choice for the price of one. "Deep saturated" + "simple round black eyes, no eyelashes" fixed the colour and the eyes in all three. **The owner picked B.** |
| 2026-10-29 | `frostfox-3d-blender-v1.png` | **Rejected: "looks very shit and nothing like the photo".** Hand-built in Blender from spheres and cones. See section 9. |
| 2026-10-29 | `snowbun-v1.png` | First pet made from sections 3 + 4 unchanged (builder's Figma file). Same family as Frostfox: matte clay, chunky clumps, same eyes and light; deep bubblegum pink; earmuff ears with pom-poms read at once. Fills a bit more of the frame than Frostfox. **Approved by the owner.** **Download problem, solved:** the cloud sandbox's network blocks `www.figma.com`, so `image.url` gave 403. Workaround: `get_screenshot` on the image's node with `maxDimension = 1024`, `contentsOnly = true`, `enableBase64Response = true` returns the full 1024 px PNG inline (free, no credits), and the session saves it as a file. |
| 2026-10-29 | `waddles-v1.png` | Sections 3 + 4 unchanged. Midnight navy bowling-pin body, long red-and-white knit scarf, yellow beak and feet. Passes every check. Waiting for the owner. |
| 2026-10-29 | `mittenkit-v1.png` | Sections 3 + 4 unchanged. Sunny orange, red-and-cream bobble hat and mittens, curled tail. **Small drift:** the eyes are dark brown with a pale rim, not the plain black eyes of Frostfox. Waiting for the owner (redo only if they mind). |
| 2026-10-29 | `pupcicle-v1.png` | Sections 3 + 4 unchanged. Lemon yellow, white frosting drips with rainbow sprinkles, bite out of one ear, popsicle-stick tail. Passes every check. Waiting for the owner. |
| 2026-10-29 | `blizzard-yeti-v1.png` | Sections 3 + 4 unchanged. Lavender shaggy clumps, glowing ice shoulder plates and crown, floating snowflakes. The floating snowflakes must be painted out of the 3D input image (loose bits confuse image-to-3D). Waiting for the owner. |
| 2026-10-29 | `aurora-owl-v1.png` | Sections 3 + 4 unchanged. Emerald clumps, aurora-ribbon wings in green/pink/violet, glowing snowflake on the chest, light motes. Eyes have a green rim (fine for a Mythic). Light motes must be painted out of the 3D input image. Waiting for the owner. |
| 2026-10-29 | `snowglobe-drake-v1.png` | Sections 3 + 4 unchanged. Ruby red, gold horns, glowing snow globe with a village on its back. **Two checks to flag:** blunt cream claws on every toe (Pet Rules › 3 says no claws out), and the village has a steeple-like tower with a plain point on top (not a cross; symbols check passes, but the owner should look). Waiting for the owner. |
| 2026-10-29 | `snowy-meadow-lineup-v1.png` | Line-up made with `prototype/ice-ray-for-pets/tools/lineup.py` (cut-out by flood fill from the border, never a global threshold): concepts Common → Secret scaled by size class, each in an ice-cube tint, and 48 px silhouettes. All 8 main colours differ and read through the cube tint; all 8 silhouettes differ. Lavender (Yeti) and lemon (Pupcicle) are the palest in the cube. Made locally, not in the Figma file. |
| 2026-10-29 | (all 8 Meadow) | **Owner approved the whole Meadow family** ("all of the pets look good"). |
| 2026-10-30 | `frostfox-3d-roblox-v1.glb` | Frostfox trimmed 19,810 → 7,499 triangles, textures 2048 → 1024 px (`tools/node/optimize.mjs`). Still matches the concept (`frostfox-concept-vs-3d-roblox-v1.png`). |
| 2026-10-30 | `snowbun-3d-rodin-v1.glb` → `snowbun-3d-roblox-v1.glb` | Rodin V2, **"8K Quad"** setting (gives about 14,600 triangles, not 8,000), 36 credits. Trimmed to 7,500. Matches the concept closely (ears, pom-poms, face, chest); the back of the head is plainer. Input was the concept PNG by raw GitHub URL (public repo), which Weave accepts. |
| 2026-10-30 | Waddles 3D | Run started (prediction `f700b615-bd5b-40f2-85bf-8a343bc50609`), not downloaded yet. **Then Weave refused more runs: the free Weave plan allows only 2 model runs.** The other 5 Meadow pets and every other zone need a paid Weave plan. |
| 2026-10-30 | Pine Forest, 8 pets | Sections 3 + 4 unchanged, Conehog first, then the rest. All pass. `bloomhorn-stag-v1.png` had eyelashes and pink-rimmed eyes (drift) → `bloomhorn-stag-v2.png` with "plain solid black round button eyes, no eyelashes and no coloured rim" added to the pet block: fixed. Line-up `pine-forest-lineup-v1.png`. |
| 2026-10-30 | Sunny Beach, 8 pets | Puffsy first, then the rest. All pass; Starbit came out as a flat star rather than standing on two arms (still reads). **The Figma Starter plan hit its MCP tool-call limit** after these, so Glowfin, Reefback Turtle, Prismapus and Beacon Orca are only saved as 256 px previews (`pets/thumbs/`); `tools/fetch_pending.sh` downloads the full PNGs from any machine that can reach www.figma.com, and `tools/fetch_pending.ps1` does the same on the owner's PC (links expire about 2026-11-06). Desert Dunes and Volcano not generated yet. |

## 8. Still to decide
- **Pets per zone:** the brief says 7 + 1 Secret per zone (40 at launch, plus about 30 hybrids). The owner asked if 8 is enough; decide before generating the zones.
- **3D method:** being tested (section 9).

## 9. Concept → 3D model

> [!danger] Never hand-build pets
> A 3D pet must start from the approved concept image with an **image-to-3D generator**, and is judged side by side against that image. Hand-building from primitives (spheres, cones) was rejected outright.

| Method | Status | Result |
|---|---|---|
| **Figma Weave image-to-3D** (`weave_find_model` → `weave_run_model`) | testing on Frostfox (2026-10-29) | Needs the Figma account linked to Weave (https://app.weavy.ai/settings?section=profile). Models found, approximate Weave credits per run: **Rodin V2 ~36** (can output a Roblox-sized 20K-triangle mesh), Trellis ~2 (rough test), Trellis 2 ~30, Hunyuan 3D V2.0 ~18, V2.1 ~25, V3 ~80, Meshy V6 ~96. Input must be an https URL or an asset uploaded with `weave_upload_asset`. Always show the cost and get an OK before each run. |
| **Blender `generate_3d` from the concept image** (Tripo / Hunyuan3D / Hyper3D) | not tested: all generators are **off** in the Blender MCP addon (addon also out of date: `uvx mcp-for-blender install-addon`) | Needs a provider switched on (own API key, or MCP for Blender Premium). |
| **Roblox Studio `generate_mesh`** | not tested: Studio was not open | Text prompt only (it can't see the concept image), max 20,000 triangles, lands in Roblox as a textured MeshPart. Fallback only. |
| **Blender by hand** (primitives) | **rejected** | Looked like a balloon toy, nothing like the concept. Don't use. |

Roblox limits for any method: **under 8,000 triangles per pet** is the target (20,000 is the hard cap for one mesh), colours must survive the upload (texture or vertex colours), and imported FBX comes in 100x too big (scale 0.01).

### Result: Rodin V2 on Frostfox (2026-10-29), the first method that works
- **Input:** `frostfox-clay-v1.png` (1024², pet centred on white), uploaded with `weave_upload_asset` (POST the file as multipart `file=` to the returned `submitUrl` with header `Authorization: Bearer <token>`), plus a short text prompt describing the pet.
- **Settings:** model **Rodin V2** (`957b4051-2080-45cb-bf6a-163325d6285f`), `quality_mesh_option = "20K Triangle"`, `material = "All"`, `preview_render = true`. **36 Weave credits**, about 2 minutes.
- **Output:** `frostfox-3d-rodin-v1.glb`: one textured mesh, 19,810 triangles, faces -Y, about 1 × 1.8 × 1.7 units. Comparison: `frostfox-concept-vs-3d.png` (concept left, 3D render right).
- **Verdict (mine, waiting for the owner):** matches the concept closely: clay fur clumps, giant tail, crystal, forehead gem, eyes and white muzzle all came through, back and sides are filled in sensibly. Small losses: the smile is a bit less clean and the crystal and gem are only painted, not glowing.
- **Still to do for Roblox:** get it under the 8,000-triangle target (try `"8K Quad"` on the next pet, or decimate in Blender), make the crystal and gem glow in Studio (Neon part or a `PointLight`/`SurfaceAppearance` emissive), then upload as a MeshPart and check it inside the ice cube at 30 studs.
