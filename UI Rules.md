# UI Rules

The rules every Roblox game UI follows. They come from what you've approved so far, from [[Lessons]], and from the useful parts of the ui-figma-roblox skill (see the Sources section at the end). Style name: **Chunky Pop**. Live demo: https://claude.ai/artifact/NDTHMTDGGSjQv96j6ynS9w

## Screen layout
- **At most 5 HUD items.** Too much UI is bad. The default HUD is 2 items: the menu tile grid and the coins.
- **Menu tiles:** a 2-column grid, vertically centered on the left edge. Up to 6 tiles, and only as many as the game needs. If they don't fit, the last one becomes "More".
- **Coins:** bottom-left corner. On touch screens they sit just above the thumbstick.
- **No HUD action button.** Open, talk and buy prompts float on the objects in the world, showing the key (E / X) on PC and console.
- **Popups:** centered horizontally, a little above the vertical middle, one at a time, with the rest queued.
- **Everything stays inside the safe area** and clear of Roblox's top bar, thumbstick and jump button.
- **One owner:** only the `Screen` module places HUD elements. Nothing else sets positions.
- **Not done until** the automatic overlap check passes at phone (844×390), tablet (1024×768) and PC (1920×1080).

## Look (Chunky Pop)
- **Blocks:** every button, tile and panel is a block, meaning a colored face sitting on a darker lip with one thick dark outline (ink `#1b1433`). Pressing pushes the face down onto the lip, then it springs back with a click sound.
- **Faces** get a soft top shine and a faint dot pattern. Keep any texture **behind** labels and icons, and quieter than them.
- **Color always means something:** green = go/yes, red = close/no, yellow = coins/rewards, blue = info. Each menu tile has its own color. No one-off colors: everything comes from `Theme`.
- **One small shared set** of fills, gradients, outlines, shadows, corner radii and spacing, reused everywhere. Don't put every effect on every element.
- **Depth offsets** (lip, drop shadow) stay small and the same everywhere.
- **Text:** Fredoka, short, white with a dark outline. Labels must stay readable over any texture.
- **Center the visible shape** of icons and text, not their bounding box. Optical centering beats math centering.

## Icons
- **Painted, not modeled.** Icons are painted-style illustrations generated with Figma `generate_image` (model `gpt-image-2.5-sunburst`, Figma file "Chunky Pop Icons"). Blender block renders were rejected as "low poly".
- **Fixed style prompt (reuse word for word, change only the subject):** "Painted digital illustration style of high-end casual mobile game icons: toy-like chunky proportions, one thick even near-black outline around the whole silhouette, thinner dark lines for inner details, soft 3D painted shading lit from the top-left with a darker bottom-right side and small crisp white highlights, rich saturated colors, clearly rendered materials. Centered with generous empty space around it. Plain flat pure white background, no shadow on the ground, no text, no frame, no border, no background plate."
- **Cleanup (always):**
  - Cut out the white background by flood fill from the borders. Enclosed holes (like a gear's middle) are cleared one by one, never by a global rule, because a global rule ate the egg's shell.
  - Trim and center at 80% of a 1024 px square, then add a 20 px ink ring (`#1b1433`).
- **Files:** `prototype/starter-kit/icons/ai/<name>.png` (1024 px, for Roblox ImageLabels), `<name>_src.png` (the original generation), and `.webp` (256 px, for web demos).
- **One main color per icon.** Each icon contrasts with its tile color (for example a blue bag on the orange Shop tile).
- **Every coin in the UI is the same coin image:** the counter, the flying coins and the price tags.
- **Motion** is a 2D tween on the image (wiggle on hover or badge, pop on gain), never a 3D spin.
- **Each generation costs Figma AI credits.** Confirm batches with the user.

## How to build a screen
1. Clarify only what matters (which screen, what it contains). A user reference overrides defaults, but we take ideas from it, not its look.
2. Design in Figma at 1920×1080 with named layers (`shop-frame`, `product-card`, `currency-display`).
3. Build large forms first: panel → header → content → text → icons → texture → polish.
4. Perfect **one** card or button, then duplicate it and change only the content and category color.
5. Check gaps with real measurements, not by eye.
6. After scaling anything, recheck text size, outline weight, shadow distance and icon size one by one.
7. Keep the original art and editable copies before flattening anything.
8. Prototype the motion in the HTML demo, then port.

## Review checklist (before showing anyone)
- [ ] Spacing and padding are the same everywhere
- [ ] Labels are readable over texture and effects
- [ ] Outlines aren't oversized, and there aren't too many effects
- [ ] No clutter, clipping, or misaligned text
- [ ] Hierarchy is clear at full size **and** zoomed in
- [ ] Overlap check passes on phone, tablet and PC
- [ ] Layer and instance names are clear and editable

## Roblox porting notes
- **Sizing:** Scale only (no Offset), plus `UIAspectRatioConstraint` and one `UIScale` per device class. Popups use UI scales of phone 1, tablet 1.2, PC 1.35.
- **Outlines:** `UIStroke` with `ApplyStrokeMode = Border`, Outside, Miter joins.
- **No Overlay blend mode** in Roblox. Bake that kind of effect into the image.
- **`UIGradient` doesn't fade tiled images.** Bake fades into the texture image.
- **Animate only what matters:** the main button of a screen, a badge, a reward. Everything else stays still (better for focus and for phone performance).
- **Icons** are `ImageLabel`s, with motion done through `TweenService` (rotation, position, size).
- **Be honest about status:** it's a mockup until it's built and play-tested in Studio. Never call it "done in Roblox" before then.

## Assets and licenses
- Use our own art (painted generations and Blender renders) by default.
- A "free" label is **not** permission to reuse. For any third-party asset, keep the source URL and creator, and confirm the rights before a game is published.
- We do **not** use the ui-figma-roblox asset pack: most of it has no clear license.

## Sources
- Our decisions and feedback: [[Lessons]]
- Hit-game research: [[Hit Games 2026-10]]
- ui-figma-roblox skill (rules and workflow only, no assets): https://github.com/grim-technologies-arch/ui-figma-roblox

## Status
- **2026-10-29:** the user says it is "starting to be perfect", so UI work is paused. This is **a path to the perfect UI, not the final version for every game.** Each game adapts it to its own theme (colors, panels, icons) and keeps raising the bar. Don't stamp the demo onto a game unchanged.


## Added 2026-10-29 (Bounce for Eggs test)
- **World prompts never sit on a HUD item.** A prompt that follows a 3D object (Hatch button, odds, "need more") is pushed right of the tile grid, below the goal bar and above the coins. In the test the Hatch prompt slid under the Index tile. In Roblox: clamp the BillboardGui's screen position, or switch to a ScreenGui prompt placed by the `Screen` module.
- **The goal bar** (one named goal + "have / need") sits top center below the Roblox top bar and counts as one of the 5 HUD items. It never starts empty.
- **Odds chips sit under the buy button** at the egg: one colored dot per rarity + its %, always the true odds.
- **Phone means landscape:** check 844×390, not portrait.

## Added 2026-10-29 (vault check)
- **No text emojis** (🙂 ⭐ 🔔) anywhere in UI, alerts, toasts or signs. Use a painted icon instead. Alerts use plain direct words.
- **Why not Peckwood:** the earlier rule followed the Peckwood Figma file (squared steel keycaps). Chunky Pop replaced it on 2026-10-29 because the user wanted our own style, not a copy of a reference look ([[Lessons]] › Style round 2). Peckwood is still fine to look at for ideas, never to copy.
- **Blender icons are out:** they read as "low poly" next to painted art. ViewportFrame 3D models are only for showing a pet or item turning in a window, not for icons.
