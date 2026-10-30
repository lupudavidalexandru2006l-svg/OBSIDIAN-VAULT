---
created: 2026-10-30
tags: [roblox, ice-ray-for-pets, port]
status: draft, waiting on prototype QA GO
---

# Ice Ray for Pets · Port Plan

How the HTML prototype (`prototype/ice-ray-for-pets/`) becomes the Roblox game (`roblox/`, a Rojo project). Written before the port goes on, as [[Code Rules]] › 1 and 3 ask. The prototype stays the design reference: if the Roblox game changes something, update the prototype or note it under "Differences" below. Sources: [[Games/Ice Ray for Pets/Game Plan]] › 18, [[Code Rules]], [[UI Rules]] › Roblox porting notes.

## 1. Owner list (one owner per thing)
Nobody but the owner changes a thing. Everyone else calls the owner or listens to its signal.

| Thing | Owner | Side |
|---|---|---|
| Save data (load, save, wipe, migrate, session lock) | `DataService` | server |
| Remotes (create, type checks, rate limit) | `Remotes` | server |
| Analytics calls | `AnalyticsSvc` | server |
| Player position, zone, walk speed, "what am I doing" | `PlayerTracker` | server |
| World parts: pens and plots, bridges, gates, gift box, boards | `WorldService` | server |
| Wild pets (spawn, odds, pity, wander, despawn) | `WildPetSpawner` | server |
| Freezing (prompt checks, pose, hold time), the ice bridge spot and its timer | `FreezeService` | server |
| Carried cubes and melting, Super Freeze offer | `CarryService` | server |
| Coins, income, banking, welcome back, daily gift (connects the gift box prompt) | `PenService` | server |
| Upgrade prices and buying | `ShopService` | server |
| Index pages and page rewards | `IndexService` | server |
| Big Chill | `EventService` | server |
| Robux: one `ProcessReceipt`, PolicyService check | `MonetizationService` | server |
| Boards (OrderedDataStore), leaderstats | `LeaderboardService` | server |
| Camera | `CameraController` | client |
| HUD placement (where every GUI piece goes) | `Screen` | client |
| HUD contents (coins, temp chip, goal bar, tiles) | `HudController` | client |
| Popups (shop, index, settings, gift, welcome) | `PopupController` | client |
| Pet visuals (models, wander, dazed spin, cube look) | `PetVisuals` | client |
| Effects (beam, bursts, Big Chill snow) | `EffectsController` | client |
| Sounds and music | `SoundController` | client |
| Settings (music, sound, reduced motion, low graphics, °C/°F) | `SettingsController` | client, saved on the server |
| Input (keyboard, touch, gamepad) | `InputController` | client |

## 2. Prototype piece → Roblox place → owner
Status: **done** = written (not yet run in Studio), **todo** = not written.

| Prototype (`src/`) | Roblox place | Owner | Status |
|---|---|---|---|
| `config.js` Config, Theme, PetDefs | `ReplicatedStorage/Shared/Config, Theme, PetDefs` | shared | done (all 40 pets) |
| `world.js` zoneAt, heatAt, meltRate, temperatureAt | `ReplicatedStorage/Shared/WorldRules` | shared | done |
| `server.js` AnalyticsSvc | `ServerScriptService/Server/Services/AnalyticsSvc` | AnalyticsSvc | done |
| `server.js` load/save | `.../DataService` | DataService | done |
| `server.js` setPosition, tickPlayerZone | `.../PlayerTracker` (uses the server's own HumanoidRootPart position) | PlayerTracker | done |
| `scenery.js` pens, bridges, gate | `.../WorldService` (4 plots, Forest gate by collision group) | WorldService | done |
| `server.js` spawner, pity, shownOdds | `.../WildPetSpawner` | WildPetSpawner | done |
| `server.js` beginZap / endZap, ice bridge | `.../FreezeService` (listens to `ProximityPromptService`, server checks) | FreezeService | done, needs EventService |
| `server.js` tickCarry, melt, Super Freeze mock | `.../CarryService` | CarryService | done, needs EventService |
| `server.js` bankCubes, income, welcome, gift | `.../PenService` | PenService | todo |
| `server.js` buyUpgrade | `.../ShopService` | ShopService | todo |
| `server.js` completedPages | `.../IndexService` | IndexService | todo |
| `server.js` tickChill | `.../EventService` | EventService | todo |
| `buySuperFreezeMock` | `.../MonetizationService` | MonetizationService | todo |
| `server.js` boards, fake rivals | `.../LeaderboardService` (real OrderedDataStores, no fake rivals) | LeaderboardService | todo |
| `client.js` camera | `StarterPlayerScripts/Client/CameraController` | CameraController | todo |
| `client.js` pets, cubes, beam, bursts | `.../PetVisuals`, `.../EffectsController` | client | todo |
| `hud.js` + `index.html` CSS | `StarterGui` ScreenGuis built by `Screen` + `HudController` + `PopupController` | client | todo |
| `audio.js` | `.../SoundController` (ids in `Config.sounds`) | SoundController | todo |
| `input.js` | `.../InputController` + ContextActionService | InputController | todo |
| `scenery.js` look (sky, terrain, trees, props) | Built in Studio: Terrain, Lighting, models | owner session in Studio | todo |
| (not in the prototype) rebirth | `.../RebirthService` (Game Plan › 18) | RebirthService | later layer, after the first Studio QA GO |
| `bot.js`, timer panel, exploit test | Server rule tests + dev commands locked to Studio (`RunService:IsStudio()`) | QA | todo |

## 3. Remotes
Clients send intent only. Every handler type-checks, checks can-do-it-now, rate-limits and decides on the server ([[Code Rules]] › 6).

| Client → server | Checks |
|---|---|
| Freeze: ProximityPrompt `Triggered` (no RemoteEvent) | server distance from its own root part, pet still wild, not already zapping, cube room, Forest unlocked for zone 2 pets |
| `BuyUpgrade(id)` | id in the upgrade list, below max level, coins looked up on the server |
| `CollectWelcome()` | a welcome is waiting; grant + "claimed" stamp in one `UpdateAsync` |
| `RequestSuperFreeze(petId)` | offer belongs to this player, not used this run, pet still dazed, in range; then `PromptProductPurchase` |
| `SetMenuOpen(bool)` | boolean; only changes "lastAction" for analytics |
| `ShopOpened()` | rate-limited; analytics only |
| Gift: ProximityPrompt on the gift box | waiting since the last UTC day; grant + stamp in one `UpdateAsync` |

| Server → client | Carries |
|---|---|
| `Data` | the player's coins, upgrades, pets, pages, settings (on change) |
| `Notify` | short messages: "Pen full", "Need 120 more", gate notice |
| `BoardRank` | your rank on each board, or "not in the top 100 yet" |

Everything else replicates as Attributes (pet `State`, `Pose`, `Mut`, `OfferUserId`; cube `LifeFrac`; world `IceBridgeUntil`, `ChillUntil`), so clients draw it without asking.

## 4. Analytics (step 5b)
One list in `Config.analytics`; `AnalyticsSvc` refuses names not in it.
- **Funnel:** 1 joined, 2 first zap, 3 first freeze, 4 first carry home, 5 first bank, 6 first coins spent, 7 first rare pet, 8 first new zone.
- **Events:** `cube_melted` (value: studs from home; pet, tier, zone), `pet_banked` (carry seconds; pet, tier, pose), `zone_entered` (zone), `shop_opened`, `offer_shown` (offer, pet, tier), `offer_bought` (Robux; offer), `session_end` on PlayerRemoving (session seconds; zone, last action, carrying a cube).

## 5. Leaderboards (step 5c)
- Boards: **Most pets frozen** (all time), **Rarest pet found** (all time), **Coins earned this week** (resets every Monday, UTC calendar day).
- OrderedDataStore per board (`LB_v1_` prefix, weekly key carries the week id), every call in `pcall` with retries; boards read every 60 s, each player's scores written at most every 120 s.
- Display names only; a name that can't be fetched shows "A player". Scores come from the server's own counters, never from the client, and are clamped to what's possible.
- `leaderstats`: Coins, Pets.
- Optional cosmetic: a glowing name plate for the weekly top 3. Never coins or pets.

## 6. Differences from the prototype
- **4 plots per server.** Each player gets their own pen on one of 4 plots around the hub; the prototype has one player.
- **Freezing uses ProximityPrompts** (custom style) so touch, gamepad and keyboard work the same; the hold time is the prompt's `HoldDuration`, decided by the server from the ray level.
- **The Forest gate opens per player** (collision groups), so one player unlocking it doesn't open it for others.
- **Real leaderboards,** no fake rivals.
- **Super Freeze is a real developer product** (15 R$), granted only inside `ProcessReceipt`, saved before `PurchaseGranted`.
- **Dev commands** (skip time, grant coins, spawn an Epic) only work in Studio.

## 6b. From the prototype QA (2026-10-30, [[Games/Ice Ray for Pets/Prototype QA]])
- **Already ported:** the Forest zone starts at the gate; saves are type- and range-checked; funnel step 4 needs a real trip; near pets and Rare+ in the far half; the Super Freeze offer has no hidden timer and shows once per run; a held pet acts at half speed; ice bridge spots on both banks with a push to the bank when it ends; bought cubes in the save (`superCubes`) and back after a rejoin; `lastBest` in the save.
- **Super Freeze purchase:** `MonetizationService.ProcessReceipt` calls `CarryService.superFreezeOffer` (which writes `superCubes`), then `DataService.saveNow`, and only then returns `PurchaseGranted`.
- **PenService:** the gift box opens after the first bank; "not yet" messages have a 2 s cooldown; the welcome back shows `lastBest`; the last pet before a gate spawns close by; banking takes the cubes with `CarryService.takeAll` and hands back any it can't bank.
- **LeaderboardService:** scores clamped with `Config.leaderboards.limits` (≤ 1 freeze a second since the account was made); weekly coins only for this week's id.
- **Others' wins seen by the server** (Game Psychology 10, Game Plan 14): a Legendary or better bank sends a server-wide banner and a light pillar over that player's pen.
- **Pen upgrade** (+5 slots, Game Plan 11) before launch; the prototype just uses 100 slots.
- **Gamepad:** `GuiService.SelectedObject` for menus, ButtonB closes, ButtonY presses the Super Freeze button.

## 7. Owner items (a helper can't do these)
- Open the Rojo project in Studio on the owner's PC (`rojo serve roblox/default.project.json`) and run the Studio QA.
- Create the **Super Freeze** developer product (15 R$) and paste its id in `Config.monetization`.
- Optional: a badge for the weekly top 3 (`Config.leaderboards.weeklyBadgeId`).
- Upload the pet models (the Roblox GLBs under 7,500 triangles) and paste the asset ids into `PetDefs`.
- Pick or upload sounds and paste the ids into `Config.sounds` (0 = silent until then).
- Real-phone test after the Studio QA, and a real controller test (prototype QA could only use a fake gamepad).

## 8. Order of work
1. Prototype QA → GO ([[QA Rules]] › 1). No more Roblox code before it.
2. Finish the server: EventService, PenService, ShopService, IndexService, MonetizationService, LeaderboardService.
3. Type-check everything until clean: `roblox/tools/typecheck.sh` (luau-lsp with the types file from the same release; see the script).
4. Client: InputController, CameraController, Screen + HudController + PopupController, PetVisuals, EffectsController, SoundController, SettingsController.
5. Server rule tests (spawner odds, pity, melt time, prices, welcome cap, gift streak, weekly reset day).
6. Studio session on the owner's PC: build the world look, insert models, then Studio QA solo and with 2+ players in Start Server ([[QA Rules]] › 7, 8).

## Status
- **2026-10-30:** written. Server half about 60% done in `roblox/src` (not yet run in Studio). Waiting on the prototype QA verdict.
- **2026-10-30:** first strict type check of the written code: 15 problems fixed, among them a require loop (WildPetSpawner ↔ FreezeService), now broken by FreezeService listening to `ProximityPromptService` instead. Only the missing EventService is left.
