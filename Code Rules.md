---
created: 2026-10-29
tags: [roblox, code, luau, rules]
status: draft, not yet used on a ported game
---

# Code Rules

How every game's Luau code is built in Roblox Studio (Stage 2 of the pipeline). Earlier games had systems that overwrote each other; these rules exist so that can't happen again. Related: [[Game Design Rules]], [[UI Rules]], [[Lessons]], [[Home]].

> [!summary] The short version
> **One owner per thing, the server decides everything that matters, and a child's progress is never lost.** Every system is a module that starts in two passes (Init, then Start). Every number lives in `Config`. Every remote is checked like the client is lying.

## 1. One owner per thing
- **Every shared thing has exactly one owner module:** camera, HUD layout, coins, inventory, pets, saving, sounds, the opening show. Nobody else changes it.
- **Other systems ask the owner** (call its function or listen to its signal). They never set its values directly. If two scripts both set `Camera.CFrame` or a GUI's `Position`, that's the bug.
- **The `Screen` module is the only thing that places HUD elements** (see [[UI Rules]] › Screen layout). Other UI code builds the contents, `Screen` decides where it goes.
- **Before adding a system, search for one that already does it** (`script_grep`, `search_game_tree`). Extend it, don't build a second one.
- **Write the owner list** at the top of the game's port plan, so it's clear who owns what before any code exists.

## 2. Startup: Init, then Start
- Each system is a ModuleScript returning a table with `Init()` and `Start()`.
- One loader Script on the server and one LocalScript on the client require every module, call **every `Init()` first** (set up state, create remotes, no talking to other modules), then **every `Start()`** (connect events, use other modules).
- This means no module ever uses another one before it's ready, and the load order of files doesn't matter.
- No module does work at require time (no loops, no `WaitForChild` chains at the top level).

## 3. Where things go
| Thing | Place | From the prototype |
|---|---|---|
| Game rules, rewards, rolls, saving | `ServerScriptService/` (server modules + one loader Script) | functions marked `// SERVER` |
| `Config`, `Theme`, shared types | `ReplicatedStorage/Shared/` | the `config` object |
| RemoteEvents | `ReplicatedStorage/Remotes/` (created by the server in `Init`) | `emit("...")` calls |
| Input, camera, effects, sounds | `StarterPlayerScripts/` (client modules + one loader LocalScript) | code marked `// CLIENT` |
| ScreenGuis | `StarterGui/` | the HTML HUD and popups |

- **Write the port plan first:** each prototype piece → its Roblox location and owner.
- Keep the prototype as the design reference; if the Roblox game changes, update the prototype or note the difference.

## 4. Luau style
- `--!strict` at the top; types on function parameters, returns and module tables.
- `task.wait`, `task.spawn`, `task.delay`, `task.defer`. Never `wait`, `spawn`, `delay`.
- Get services once at the top: `local Players = game:GetService("Players")`.
- **No magic numbers or one-off colors in logic.** Speeds, prices, odds, timings, sizes and colors live in `Config` / `Theme`.
- Prefer events over polling. Never a `while true do` without a yield.
- Client: `WaitForChild` with a timeout; `FindFirstChild` guards for anything that may be missing.
- Clear names over comments; comment only the "why". Simplest working version first.

## 5. Cleanup
- **Store every connection** and `:Disconnect()` it when the player leaves, the round ends or the UI closes. Use a small Maid if the same cleanup repeats.
- Per-player state is a table keyed by `Player`, cleared in `PlayerRemoving`.
- **Shows and sequences** (the opening show, cutscenes) run their cleanup even if a step errors (`pcall` the steps, cleanup after), and restore the camera to its owner.

## 6. The server decides (remotes)
The client is untrusted: it can send anything, any number of times.
- **Clients send intent** ("hatch egg 2"), **never outcomes** ("give me a Mythic", "I have 500 coins").
- For every `OnServerEvent`:
  1. **Type-check** every argument (`typeof`, finite numbers in range, short strings, ids from a whitelist).
  2. **Check the player can do it now:** distance to the object, ownership, cooldown, unlock, game state, enough coins (looked up on the server).
  3. **Rate-limit** per player; drop spam quietly.
  4. **Decide the result on the server** (rolls, prices, rewards), then tell the client what happened.
- Ignore bad calls quietly; don't error loudly.
- Use RemoteEvents, not server → client RemoteFunctions (a client can hang them forever).
- The client may play effects early, but the server's answer wins.
- Any player-written text shown to others goes through `TextService` filtering. No free-text systems.

## 7. Saving (never lose a child's progress)
- Every DataStore call in `pcall` with 3-5 retries and backoff (`task.wait`).
- **Load on join; the player earns nothing until the load succeeds.** If it fails after retries, kick with a friendly message instead of playing on defaults.
- **Never save defaults over real data:** only save a player whose load succeeded.
- Save on `PlayerRemoving`, in `game:BindToClose` (all players, bounded wait), and autosave every 60-120 s. A `saving[player]` flag stops double saves.
- `UpdateAsync` for anything that changes (coins, counters, claims).
- **Stamp a claim in the same save as the grant.** A welcome-back or daily gift writes "claimed at" and the reward in **one** `UpdateAsync`. In the Bounce for Eggs test, saving the claim time separately paid the gift again on every quick rejoin (coins 1,900 → 5,022).
- **Block saving while wiping.** A reset must turn off save-on-leave first, or the old save comes back (seen in the test).
- Version the data (`Version` field + a migrate step) and merge in a defaults template, so old saves get new fields.
- Save plain data: numbers, strings, tables, item ids. Never Instances.

## 8. Assets from Blender
- Export FBX, upload with `prototype/boo-town/tools/upload_model.ps1` (prints `ASSET_ID=`), insert with the Studio MCP `insert_asset`.
- Imported FBX arrives 100x too big (`ScaleTo(0.01)`) and without material colors: re-apply colors and Neon in a Luau pass.
- Under 20k triangles per mesh.
- The Open Cloud key is in the env var `ROBLOX_OPEN_CLOUD_KEY`. Never print it.

## 9. Working in Studio
- The project lives in Studio, not on disk. Work through the Studio MCP tools: `search_game_tree`, `script_read`, `script_grep`, `multi_edit`, `start_stop_play`, `get_console_output`.
- **Read existing code before changing anything**, and check what depends on it.
- Change only what the task needs. Don't rewrite working systems without a reason.
- After a change: play-test, read the console output, then do the QA checks below.

## Checklist before calling code done
- [ ] Owner list written; no two scripts set the same thing
- [ ] Every module has Init/Start; nothing runs at require time
- [ ] `--!strict`, `task.*` only, no magic numbers outside `Config` / `Theme`
- [ ] Every connection is cleaned up on leave / round end / close
- [ ] Every remote: types checked, can-do-it-now checked, rate-limited, result decided on the server
- [ ] Spam-clicking every button changes nothing it shouldn't
- [ ] Saving: load gate, no default overwrites, `BindToClose`, autosave
- [ ] Rejoin twice fast: no gift paid twice
- [ ] Reset really wipes
- [ ] Multi-player "Start Server" test with 2+ players
- [ ] Console has no errors or warnings from our scripts

## Status
- **2026-10-29:** first draft. Gathered from the project rules, the Luau / saving / remote-security skills and the Bounce for Eggs [[Lessons]]. Not yet used on a ported game: the first port will test it.
