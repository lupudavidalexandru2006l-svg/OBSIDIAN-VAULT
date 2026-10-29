---
created: 2026-10-29
tags: [roblox, marketing, thumbnails, icons, pipeline]
---

# Game Page Art

How we make the art on a game's Roblox page (the square icon and the 16:9 thumbnails players see before they click Play), so every game has the same style. Research behind it: [[Research/Game Page Art]]. Related: [[UI Rules]], [[Lessons]].

> [!summary] The recipe
> An AI-generated scene in a **glossy-but-grounded Roblox render style** (the merge of our 1st glossy test and the tweaked test, prompt below), telling **one tiny story** with the game's real characters and items, plus **flat cartoon marks we add ourselves** ("YOU!" + red arrow, "ZZZ"). No title text. Approved by the user on 2026-10-29.

## What every game needs
- **1 icon:** 512×512 PNG.
- **6 thumbnails:** 1920×1080, JPG or PNG, **under 3 MB each**.
- Roblox allows up to 10 thumbnails. For Home page testing ("thumbnail personalization") **2-5 can be active at once**, so upload all 6, keep the best 5 active, and swap one in with each big update.

### The 6 thumbnail slots
| # | Slot | What it shows | Marks |
|---|---|---|---|
| 1 | **Story moment** (lead) | The core loop as a mini-story with a twist: the hero grabs the reward while a giant goofy obstacle sleeps / looks away | "YOU!" + arrow, "ZZZ" |
| 2 | **Reward reveal** | Close-up: the hero's amazed face + the rarest reward glowing, rays behind | none, or one short word ("MYTHIC") |
| 3 | **Glow-up** | Small plain hero on the left → huge powered-up hero on the right ("weak to OP") | one big arrow |
| 4 | **Friends** | 3-4 avatars doing the main action together, happy faces | none |
| 5 | **World** | The best-looking place or zone with the hero small in front: shows there is more to explore | none |
| 6 | **New update** | The newest pet / zone / event; swap this one with each update | one short label ("NEW PET") |

**Icon** = the same hero's face, close, + the game's main reward (a crop of the slot-2 idea), simple bold background, no text.

## Style rules
**The style is a merge of two tests:**
- **From the 1st, glossy test:** semi-gloss plastic with clean highlights, a soft colored rim light, rich candy colors, a strongly sparkling reward, patterned props (star and spot eggs), a few tiny twinkles in the sky, a close crop on a big expressive face. This is the punch that wins the click.
- **From the tweaked test:** real cast shadows, soft clouds, small blocky Roblox trees far back, a studded baseplate, no painted swirl strokes, no lens flare, no heavy bloom. This keeps it believable as a Roblox game, not "AI art".

In detail:
- **Look:** polished 3D Roblox render. Blocky Roblox avatar proportions; SmoothPlastic with a **smooth semi-gloss finish, not wet**; warm sun from the top-left with **real cast shadows** and a soft colored rim light; rich saturated candy colors; one dominant hue per image.
- **Stage:** a studded Roblox baseplate (or the game's real ground), a bright gradient sky with a few soft clouds and a few tiny twinkles, a couple of small blocky trees or game props far back. Background stays simple (about 20% of the attention).
- **Effects:** **the reward sparkles strongly and is the brightest object**; everything else stays calm. No lens flare or heavy bloom.
- **Hero:** the same avatar in every image of a game (messy orange hair + blue hoodie in the template), big mischievous or amazed face, close to the camera on the left third, slightly cut by the frame edge.
- **Honest:** only characters, creatures, items and places that really exist in the game, in their real colors. Roblox forbids misleading media, and a thumbnail that over-promises loses traffic, because Roblox ranks thumbnails by players who keep playing.
- **Kid-safe:** happy or mischievous faces, sleepy or goofy giants, never scary.
- **Layout:** nothing important in the **bottom 15%** (the player count covers it); leave empty sky where the marks go; max ~5 elements.
- **Text:** no game title. Only the flat marks below, max 3 per image, never sales claims ("FREE", "50% OFF") or links.

### What we tried
| Version | Result |
|---|---|
| 1st: Glossy (wet plastic, swirl strokes, sparkles everywhere) | Punchy, but "too AI-ish" |
| 2nd: Natural (looks like an unedited in-game screenshot) | Honest, but flat and small at tile size; rejected |
| 3rd: Tweaked (satin, shadows, trees, sparkles only on the egg) | Good, but a bit too calm |
| **Final: 1st + 3rd merged** (this note) | **Approved** |

Side by side (glossy / FINAL / tweaked): `prototype/starter-kit/marketing/reference/style_compare_glossy_FINAL_tweaked.png`.

## The fixed style prompt
Generate with Figma `generate_image`, model **`gpt-image-2.5-sunburst`**, Figma file "Chunky Pop Icons" (key `AY6XGBCWJ2lKNrchkjk9DE`) or the game's own file. Thumbnails: width 2048, height 1152 (it returns 1536×864). Icon: 1024×1024.

Reuse the **style block word for word**; write only the **Scene** part per image.

**Thumbnail style block:**
> Roblox game thumbnail in the polished glossy 3D render style of top Roblox experience thumbnails, kept believable: classic blocky Roblox avatar proportions, Roblox SmoothPlastic materials with a smooth semi-gloss finish and clean highlights (not wet), warm sunlight from the top-left with real crisp cast shadows on the ground, soft colored rim light separating the subjects from the background, rich saturated cheerful candy colors, kid-friendly. Stage: a studded teal-green Roblox baseplate floor, a bright sky-blue gradient sky with a few soft clouds and a few tiny twinkling stars, and a couple of small blocky Roblox trees far in the background. Effects kept light: the reward sparkles strongly, one or two thin soft glowing magic wisps in yellow and pink curl around the creature, no lens flare, no heavy bloom. No text, no letters, no logos, no UI, no watermark, no border. Keep the bottom 15% of the frame free of important details.

(Change the stage words to the game's real ground, colors and props. The "magic wisps" line is optional: use it only when the creature or item really has magic.)

**Icon style block:**
> Roblox game icon in the polished glossy 3D render style of top Roblox experience icons, kept believable: classic blocky Roblox avatar proportions, Roblox SmoothPlastic materials with a smooth semi-gloss finish and clean highlights (not wet), soft key light from the top-left, soft colored rim light, rich saturated cheerful candy colors, kid-friendly. Simple background: a smooth gradient with bold sunburst rays, one dominant hue. The reward sparkles strongly and is the brightest object. No text, no letters, no logos, no UI, no watermark, no border. Must read clearly at 150 pixels.

**Scene part, the approved example (slot 1):**
> Scene: a tiny story. Sky blue and teal dominant hue. On the left third, close to the camera and slightly cut by the frame edge, a Roblox avatar kid with messy orange hair, blue hoodie and black pants, with a big mischievous toothy grin, tiptoes away hugging a big golden egg made of glowing Neon material covered in sparkles; the egg is the brightest object in the image. On the right two thirds, filling the diagonal, a giant chubby friendly turquoise dragon sleeps curled up on a pile of colorful eggs with star patterns and spots, eyes closed with a sweet sleepy smile, a small bubble at its nose. Empty sky above the hero's head and above the dragon's head for labels added later.

**Scene part, the icon test (slot-2 idea):**
> Scene: extreme close-up. A Roblox avatar kid with messy orange hair and a blue hoodie, face filling the lower-left half of the square, mouth wide open in a huge amazed happy gasp, eyes sparkling, holding up a big glowing rainbow-gold pet egg with a crack of light on it and sparkles bursting out. Warm orange and yellow sunburst rays behind on a magenta-to-purple gradient. The egg is the brightest object. Bold, simple, two subjects only: the face and the egg.

**Scene-writing tips:** name the dominant hue; say where each subject sits (left third / right diagonal); name the brightest object; describe faces (grin, gasp, sleepy smile); ask for empty sky where marks will go. The model tends to fill the sky: ask for the empty space explicitly, and expect to fit the marks around wings and horns.

## Steps
1. **Write one sentence per slot** from the game's real loop (what the hero does, what they get, what's in the way). Check that every thing in it exists in the game.
2. **Test first:** generate slot 1 and the icon only. Each generation costs the user's Figma AI credits, so **confirm with the user before generating the rest**.
3. **Download** the full image from the returned `image.url` (expires in 7 days) into `prototype/<game>/marketing/raw/`.
4. **Upscale** thumbnails to 1920×1080 with ffmpeg lanczos:
   `ffmpeg -i raw/x.png -vf scale=1920:1080:flags=lanczos work/x_plate_1920.png`
   Icons: `-vf scale=512:512:flags=lanczos`.
5. **Add the marks** with `prototype/starter-kit/marketing/tools/add_marks.py` (runs in Blender: `blender -b --factory-startup --python add_marks.py`). It reuses Boo Town's compositor (`boo-town/marketing/tools/`): LuckiestGuy lettering with a thick ink outline (`#1b1433`), an extruded side and a drop shadow.
   - "YOU!": white, tilted -6°, in the sky above or beside the hero, with a red curved arrow onto the hero's head.
   - "ZZZ": three blue Zs, smallest first, rising from a sleeping giant's head.
   - Copy the script per game; set the positions in 1920×1080 pixels.
6. **Check at tile size:** shrink to 267×150 (thumbnail) and 150×150 (icon). The story, the face and the reward must still read.
7. **Export:** thumbnails as JPG under 3 MB at 1920×1080, icon as 512×512 PNG, into `prototype/<game>/marketing/final/`. Keep raw plates and work files.
8. **Upload** on the Creator Dashboard (icon: Configurations > Places > start place > Icon; thumbnails: up to 10, keep 2-5 active for personalization). Test for at least 7 days before judging.

## Files
- Approved examples: `prototype/starter-kit/marketing/reference/`: `approved_thumb_story_1920.png` (the final merged style, with marks), `approved_thumb_story_plate_raw.png` (the raw generation), `approved_icon_reward_512.png`, the style comparison, and the previous tweaked version (`prev_tweaked_*`).
- Marks script: `prototype/starter-kit/marketing/tools/add_marks.py`.
- Raw generations and work files: `prototype/starter-kit/marketing/raw/`, `work/`.
- Font: `prototype/boo-town/marketing/fonts/LuckiestGuy-Regular.ttf`.

## Notes
- The icon test was made in the 1st, glossy style and was liked; the icon style block above is the same look with the merged wording.
- Boo Town's page art (`prototype/boo-town/marketing/`) is made from real Studio renders instead. Either way is fine; the rules above (story, hero, honest, marks) apply to both.
- `obsidian_patch_content` is broken (see [[Lessons]]); edit this note by rewriting it in full.
