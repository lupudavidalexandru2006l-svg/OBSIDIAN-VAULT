---
created: 2026-10-29
tags: [roblox, animation, motion, rules]
status: draft, timings are starting values
---

# Animation Rules

How everything moves: buttons, rewards, pickups, pets, the camera and the big "you got something" shows. Related: [[UI Rules]], [[Code Rules]], [[Game Design Rules]] › 7 Feel, [[Lessons]], [[Home]].

> [!summary] The short version
> **Motion always means something.** The thing to do next moves the most; everything else stays calm. Every timing lives in `Config`, reduced motion halves it, and the bigger the reward, the longer the show. A show only plays the result the server already decided.

## 1. Principles
- **One moving focal point per screen.** The next action pulses or bounces; the rest of the HUD stays still ([[UI Rules]] › Animate only what matters).
- **Motion matches value.** A coin gets a tiny pop, a Mythic gets the full show. Never a big celebration for a small result.
- **Fast in, soft out.** Things arrive quickly and settle gently (overshoot a little, then rest). Nothing makes a kid wait to keep playing.
- **Every timing is in `Config`** (`Config.motion` for small moves, `Config.show.<name>` for shows). No durations hard-coded in animation code.
- **Reduced motion** (a setting in our menu, on by default if the device asks): every duration × 0.5, no screen shake, no camera kicks, pulses stop, flashes become a soft fade.
- **Kid-safe:** no more than 3 flashes per second, no fast full-screen strobes, no shaking longer than half a second. Nothing scary: creatures pop, wiggle and smile, they never lunge at the camera.

## 2. The motion set (starting values)
One small shared set, reused everywhere, like the UI's shared fills and outlines.

| Name | Used for | Time | Easing (TweenService) |
|---|---|---|---|
| **press** | Any button: face pushes onto its lip | 0.06 s down, 0.14 s back | Quad Out, then Back Out |
| **pop** | Something appears (popup, reward, badge) | 0.25 s, scale 0 → 1.08 → 1 | Back Out |
| **close** | Something leaves | 0.15 s, scale → 0.9 + fade | Quad In |
| **pulse** | The one next action | 1.2 s loop, scale 1 → 1.06 | Sine InOut |
| **wiggle** | Icon wants attention (badge, new item) | 0.4 s, ±8° rotation, every 3 s | Sine InOut |
| **fly** | Coins/rewards flying to the counter | 0.5-0.7 s on a curve, counter pops on arrival | Quad In |
| **count** | A number going up | 0.4 s roll-up, pop at the end | Quad Out |
| **bob** | Pickups and interactive things in the world | 1.6 s loop, up 0.4 studs + slow spin | Sine InOut |
| **shake** | "Not yet" (can't afford, locked) | 0.3 s, small side shake | Linear |
| **fade** | Screen transitions | 0.25 s | Quad Out |

Tune these in play, then write the new values back here.

## 3. Shows ("you got something")
The big moments: eggs, crates, chests, rare unlocks, merges. The full beat list is in the project rules (title card → pocket stage → arrival → build-up → drop → burst → reveal → title text → exit). Here is how they are built.

### How a show runs
- **The server decides first.** The client asks ("hatch"), the server rolls and saves, then sends the result. The show only plays it. A player who leaves mid-show still has the pet.
- **A show is a list of named beats**, each with a duration in `Config.show.<name>` (e.g. `title = 0.8, arrival = 1.4, buildup = 2.5, burst = 0.3, reveal = 2.2`).
- **One `Show` module owns all shows** and the camera while a show runs ([[Code Rules]] › One owner). It hands the camera back to the camera owner at the end.
- **SKIP after the first viewing** of that show. Skip jumps to the reveal + OK, it never skips seeing what you got.
- **Cleanup always runs**, even if a beat errors or the player leaves: remove the models, restore the camera, show the HUD again, re-enable controls. One `finish()` that is safe to call twice.
- **Pocket stage:** a small arena built far from the map (or high in the sky), in the item's color. Pickups and other HUD hide during the show.
- **Camera:** looks at the reward from the far side, so the player isn't between camera and reward (learned in Bounce for Eggs, see [[Lessons]]).

### Rarity scales the show
| Rarity | Beats | Length |
|---|---|---|
| Common / Uncommon | pop, small burst, name | about 1.5 s |
| Rare / Epic | + arrival, short build-up, rays | about 3-4 s |
| Legendary | + chains / cracks build-up, slow-down, big flash, title slam | about 5-6 s |
| Mythic / Secret | the full show, light pillar, server-wide shout-out | about 7-9 s |

### Honest shows
- **No fake near-misses.** A reel or a build-up never slows on a better item than the one you got and then slides past it.
- **The build-up never lies about the result:** a common doesn't get the Mythic's chains.
- **Check Boo Town's roll reel** (`config.pets.show.tease` in `prototype/boo-town/pets/`) against this rule before it's reused.

### Beat runner (Luau sketch)
```lua
--!strict
-- Plays beats in order; skip jumps to the beats marked keepOnSkip; finish always runs.
type Beat = { name: string, time: number, keepOnSkip: boolean?, play: (ctx: any, seconds: number) -> () }

local function run(beats: { Beat }, ctx: any, finish: () -> ())
	local scale = if ctx.reduced then 0.5 else 1
	local ok, err = pcall(function()
		for _, beat in beats do
			if ctx.skipped and not beat.keepOnSkip then
				continue
			end
			beat.play(ctx, beat.time * scale)
		end
	end)
	finish()
	if not ok then
		warn("Show beat failed:", err)
	end
end
```

## 4. Characters and pets
- **Every pet and character has at least:** idle (breathing / bob), move (walk, hop or fly), happy (when you get or pet it) and one **signature move** for the reveal.
- **The signature move matches the name:** a Sun Phoenix flaps and glows, a frog hops. Same rule as "every collectible looks like its name".
- **Chunky and readable at a distance:** big poses, squash and stretch, a clear silhouette. Small twitches don't read on a phone.
- **Making them:**
  - Simple motion (bob, spin, hop, squash) is done in code on the client with TweenService or a per-frame update. No keyframe animation needed.
  - Keyframe animations: Roblox Animation Editor, or animate in Blender, export FBX with the armature and import it in the Animation Editor.
  - **Upload animations under the same owner as the game** (the user's account, or the group if the game moves to a group). Animations owned by someone else won't play.
  - Animation IDs live in `Config`.
- **In Roblox:** pets use an `AnimationController` + `Animator`; avatars use the Humanoid's `Animator`. Load each track once and reuse it; stop and destroy tracks on cleanup. Set priorities (Idle / Movement / Action) so moves layer instead of fighting.

## 5. World motion
- **Interactive things move, scenery stays calm:** pickups bob and spin, the next goal glows and pulses, the background barely moves (slow clouds, gentle water).
- **World motion runs on the client** (bobbing pickups, spinning coins, swaying trees). The server only owns where things are and who gets them.
- **Nothing moves while it's off-screen or far away.** Stop loops beyond a set distance (`Config.motion.farDistance`).
- **Particles:** use `ParticleEmitter:Emit(n)` bursts for celebrations instead of always-on emitters. Keep the count per burst in `Config`, low enough for a cheap phone.

## 6. Camera
- **The camera has one owner** ([[Code Rules]]). Shows borrow it and hand it back.
- **Moves are short and smooth:** push-ins of 0.5-1 s, a small kick (≤ 0.3 s) on a chain snap or slam. No kicks with reduced motion.
- **Never spin the camera around the player** without them asking. Kids get dizzy.

## 7. From prototype to Roblox
| Prototype | Roblox |
|---|---|
| CSS keyframes / JS tweens | `TweenService` on the GuiObject or part |
| three.js show scene | Client `Show` module + a pocket stage model far from the map, `Camera.CameraType = Scriptable` during the show |
| `config.pets.show` beats | `Config.show.<name>` |
| `reduced` flag | A player setting, saved with their data |
| `requestAnimationFrame` loops | `RunService.RenderStepped` / `Heartbeat` on the client, disconnected on cleanup |
| Sprite rays / flashes | ImageLabels or a `ParticleEmitter`, a white Frame for the flash |

## Checklist before calling motion done
- [ ] Every duration comes from `Config`; none hard-coded
- [ ] Only the next action pulses; the HUD is otherwise still
- [ ] Reduced motion: halved times, no shake or kicks, no strobes
- [ ] Shows: server result first, SKIP after the first time, cleanup works if you leave mid-show
- [ ] Rarity scales the show; no fake near-misses
- [ ] Every pet has idle, move, happy and a signature move that matches its name
- [ ] Animations are owned by the game's owner and play in a live server
- [ ] No loops running off-screen; particle bursts are phone-safe
- [ ] Camera goes back to its owner after every show

## Status
- **2026-10-29:** first draft at the user's request. Built from the project's opening-show rules, Boo Town's show code (`PetShow`: beats in config, reduced = ×0.5, SKIP after first viewing, a `finish()` cleanup) and [[Lessons]]. The motion timings are starting values, not tested yet.
