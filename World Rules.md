---
created: 2026-10-29
tags: [roblox, world, level-design, lighting, depth, rules]
status: draft, lighting values are starting values
---

# World Rules

How our game worlds are laid out, lit and given depth. Related: [[Game Design Rules]] › 8 (casino floor → theme park), [[Animation Rules]] › World motion, [[Sound Rules]] › The world, [[Code Rules]], [[Lessons]], [[Home]].

> [!summary] The short version
> **Bright, deep and easy to read.** The world is a ring you can't get lost in, the next attraction is always in view, and something to do is never more than 3 seconds away. Depth comes from real distance (haze, far scenery, layers), but the player, pickups and buttons always pop more than anything behind or in front of them.

## 1. Principles
- **Deep, never flat.** At least 4 layers from the sky to the foreground, shadows and visible thickness on everything.
- **Clarity beats depth.** The player and interactive things have the strongest contrast; background and foreground stay calmer, paler and lower-contrast.
- **Bright and warm.** Daytime sky, warm sun, soft shadows. No gloomy, dark or threatening places.
- **Light enough for a cheap phone.** Most young players are on mobile.
- **Every distance, color and speed is in `Config` / `Theme`.** No numbers in build scripts.

## 2. Layout (theme park, not maze)
- **The main loop is a ring:** spawn → reward → spend → next zone, and back past the start. No dead ends, no empty corridors.
- **The next attraction is always in view,** ahead of the player, and the camera's default direction looks toward it (in Bounce for Eggs the next island was always visible ahead).
- **Something to do within 3 seconds of walking** anywhere: a pickup, a pet, a button, a friend. Keep the world full; pace with prices, not scarcity ([[Game Design Rules]] › 3).
- **Landmarks, not maps.** Young kids find their way by big shapes (a giant tree, a tower, a fountain). Every zone has one landmark visible from far away, in its zone color.
- **A cosy hub** with hangout spots (benches, a fountain, a stage) where friends sit and show off pets.
- **Zones are gated, not walled:** a locked zone is visible, glowing and a little out of reach, so kids want it. The gate says how close you are ([[UI Rules]] › goal bar).
- **Wide and forgiving:** paths at least 3 avatar-widths wide, jumps easier than they look, low rails or soft edges near drops.
- **Falling is gentle:** anyone who falls off is put back on solid ground near where they were within a second or two. No lost progress, no "you died".
- **Edges look natural** (water, cliffs, clouds, hedges) instead of invisible walls. Where a wall is needed, make it a visible thing (a fence, a cloud bank).

## 3. Layers and parallax
| Layer | Parallax | Prototype (three.js) | Roblox |
|---|---|---|---|
| Sky + sun | 0 (fixed) | Gradient sky dome, sun disc | `Sky` skybox, `Lighting` sun |
| Far clouds | ~0.1 | Slow cloud sprites (`cloudSpeed.far`) | `Clouds` object (moves with `Workspace.GlobalWind`) |
| Distant scenery | ~0.3 | Pale islands/hills far out, in fog | Low-detail models far beyond the playable map, faded by `Atmosphere` |
| Mid set dressing | ~0.7 | Trees, rocks, houses near the edges | Normal models just outside the paths |
| Play area | 1 | The game | The game |
| Foreground | >1 | Leaves, birds, wave crests near the camera | Small near-camera details (birds, falling leaves) |

- Speeds live in `Config.parallax` (0 = fixed, 1 = play area, above 1 = foreground). In 3D the parallax comes from real distance; the numbers are for drifting things (clouds, birds) and 2D prototypes.
- **Foreground details never cover** the player, pickups or buttons. Fade or move them out of the way.
- Moving layers stay gentle; reduced motion slows or stops them ([[Animation Rules]] › 1).

## 4. Depth cues
- **Soft shadows** under every character and object.
- **Thickness:** platforms and islands have a visible side face and an underside (dirt, rock), never a paper-thin top.
- **Distant = paler and bluer:** far layers use the `...Far` theme colors (the starter kit has `grass` and the paler `grassFar`) and fade into the haze.
- **Draw order in 2D:** back to front, near things overlap far ones.

## 5. Color and lighting
- **The palette lives in `Theme`:** sky blues, grass greens, sunny yellow, warm orange, candy pink and purple. One main color per zone.
- **Interactive things use the strongest colors** (and glow or bob); scenery uses softer versions of the zone color.
- **Night themes** (like Boo Town) are allowed only candy-bright: glowing neon, a big friendly moon, purple and teal, never murky or scary. The rest of the world still reads as fun.
- **Roblox lighting, starting values** (tune per game, keep them in `Config.lighting`):
  - `Lighting.ClockTime` about 14 (afternoon sun from one side, shadows that show shape)
  - Warm `Ambient` / `OutdoorAmbient`, `Brightness` around 2-3
  - `Atmosphere` for haze: low `Density` (~0.3), a light sky-blue `Color`, `Glare` 0, a little `Haze`
  - `Clouds`: medium cover, soft and white
  - A `ColorCorrectionEffect` with a small saturation boost (about +0.1), no heavy bloom
- With an `Atmosphere` in `Lighting`, the old `FogStart` / `FogEnd` are ignored, so the prototype's fog numbers map to `Atmosphere` settings, not to fog.

## 6. Reading the world
- **Interactive = glows, bobs or has a prompt.** Scenery never glows or bobs, so kids learn what they can touch.
- **Neon is for rewards and the next goal only** ([[Game Page Art]] uses the same rule).
- **The size of things fits a kid avatar:** buttons and pads big enough to land on, doors wide enough for a group.
- **Every collectible looks like its name** ([[Game Design Rules]] › 5), from a distance too.

## 7. Performance (phones first)
- **`StreamingEnabled` on** for anything bigger than a small map.
- **Far scenery is cheap:** low-detail meshes, `Anchored`, `CanCollide` / `CanTouch` / `CanQuery` off, `CastShadow` off.
- **Meshes under 20k triangles** ([[Code Rules]] › Assets from Blender); reuse the same mesh many times instead of many different ones.
- **A Low graphics setting** (Boo Town has `lowGfx`) that hides far details and foreground extras.
- **Check on a real phone**, not just Studio's device emulator: frame rate in the busiest spot, with several players.

## 8. From prototype to Roblox
| Prototype | Roblox |
|---|---|
| `config.world.fogNear / fogFar` | `Atmosphere` density and offset (`Config.lighting`) |
| Gradient sky dome | `Sky` skybox |
| `cloudSpeed.near/mid/far` | `Clouds` + `Workspace.GlobalWind`, near birds as moving models |
| Far pale islands | Low-detail models beyond the map |
| `cameraDist`, `cameraSway` | The camera owner's `Config` ([[Code Rules]]) |
| `pixelRatioCap` | Not needed; use the Low graphics setting |
| `Theme` colors incl. `...Far` | `Theme` module, the same names |

## Checklist before calling a world done
- [ ] At least 4 layers from sky to foreground; depth shows in a screenshot
- [ ] The player, pickups and buttons pop more than anything else
- [ ] The main loop is a ring; no dead ends; the next attraction is in view
- [ ] Something to do within 3 s everywhere; one landmark per zone
- [ ] Falling puts you back nearby, quickly, with nothing lost
- [ ] Bright and warm (night only candy-bright); colors from `Theme` only
- [ ] Only rewards and the next goal glow
- [ ] All distances, colors, speeds and lighting values in `Config` / `Theme`
- [ ] Runs smoothly on a phone with several players; Low graphics works

## Status
- **2026-10-29:** first draft at the user's request. Built from the project's visual-style and depth rules, the starter kit's `config.world` (fog 40-170, camera 17.5, cloud speeds near 1.6 / mid 0.9 / far 0.4, `grassFar`), Boo Town's night palette and `lowGfx`, and [[Game Design Rules]] › casino floor → theme park. Lighting values are starting points, not tested in Studio yet.
