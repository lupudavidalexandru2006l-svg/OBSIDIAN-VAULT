# Lessons

What went wrong, why it happened, and the rule that changed because of it. Newest at the top. Every playtest, phone check and piece of feedback lands here, and then the matching rulebook note gets updated.

## 2026-10-30 · Ice Ray for Pets prototype QA (round 1 NO-GO, see [[Games/Ice Ray for Pets/Prototype QA]])
- **Three reviewers found 64 issues the builder missed,** including a guide arrow pointing backwards and nothing ever melting. **Rule:** the three-reviewer QA is worth its cost; run it before showing a build as done.
- **The arrow pointed away from the goal** because the chevron was modelled along -z and turned as if along +z. **Rule:** check every direction marker in a screenshot against where it should point.
- **A "fix" can regress:** the new movement budget allowed one 8-stud step, which hopped the thin locked-gate line. **Rule:** checks along a move, not just at its end; re-run the whole suite after every fix round.
- **A test failing after a fix can be the test, not the game:** five checks still expected the old rules, the play-tester's bridge script used the old bridge spots, and its fake gamepad mashed every button at once. **Rule:** when a rule changes on purpose, update the check to test the new rule and say so in the QA note.
- **Software rendering drops button presses** at 2-5 fps, so gamepad checks flake. **Rule:** hold fake button presses for 400 ms+, and leave the final say to a real controller (owner item).
- **The playtest bot can hide a design problem:** with pets always close, the bot never left the Meadow and never banked a Rare, so its timings said nothing about the Forest. **Rule:** when spawning changes, re-check that the bot still plays like a kid (chases glows, goes to the new zone).
- **Hiding a "+0" made a box grow later** (the +N/s line appears with the first income), which broke the phone layout. **Rule:** the Screen layout re-runs when a HUD box changes size.

## 2026-10-30 · Ice Ray for Pets prototype: reading, looks and tooling
- **Five rule notes were skipped at the start** and the owner had to ask twice ("did u even read the vault?"). The prototype then broke rules those notes set. **Rule:** read every note in the vault root (including Research and Brainstorm) before the first line of code, and name the notes read in the first progress message.
- **"The game looks shit"** after the first playable build: flat colours, bare primitive props, default lights, a plain ground plane. **Fix that worked:** gradient sky, noise terrain with vertex colours, merged and instanced props with rounded shapes, ACES tone mapping, soft shadows that follow the player, room-style environment light, and the painted icons in the HUD. **Rule:** a prototype gets its look pass before the owner first sees it, not after.
- **Shadows ran at 1.5 fps in the software renderer.** **Rule:** every prototype has a Low graphics setting from day one (no shadows, fewer props), remembered between visits ([[QA Rules]] › 4 slow phone).
- **A tree filled the screen at the river.** **Rule:** props between the camera and the player sink out of the way; check the camera at every landmark.
- **Controls were mirrored** because the camera looks south. **Rule:** test movement against the screen (push right, go right), never against the world axes.
- **The rate limit used real time,** so the sped-up bot had calls dropped. **Rule:** rate limits run on the same clock as the game.
- **The helper tools need Python and Node,** which the owner's PC doesn't have. **Rule:** cloud-only tools say so in a `tools/README.md`; anything the owner must run at home (like downloading expiring art links) gets a PowerShell version.

## 2026-10-29 · Building Ice Ray for Pets in a cloud session
- **The vault notes disagreed on Secret pets:** the Game Plan said Secrets only in zones 4-5, the Pet Brief gave every zone one. **Owner's call:** first zones 4-5 only, then (once it meant cutting Snowglobe Drake) a Secret in every zone. **Rule:** when two notes disagree, ask, show what each answer costs (here: losing a designed pet), then fix both notes the same day.
- **The cloud sandbox blocks `www.figma.com`,** so a `generate_image` result can't be downloaded with curl (403), and the network settings had no edit option for the owner. **Fix that worked:** `get_screenshot` on the new image's node (`maxDimension 1024`, `contentsOnly true`, `enableBase64Response true`) sends the full 1024 px PNG inline for free. **Rule:** in a cloud session, fetch every generated image this way straight after generating it ([[Games/Ice Ray for Pets/Pet Art Recipe]] › 7).
- **Studio, Blender and Obsidian MCPs aren't in a cloud session.** The vault is edited as files in its git repo instead; Studio work needs a session on the owner's PC.
- **Network changes only reach new sessions.** After the owner allowed figma.com, this session still got 403s; a helper session started later downloaded the Snowbun GLB fine. **Rule:** after changing an environment's network, start a fresh session for the downloads.
- **Free plans ran out mid-zone.** The Weave free plan allows only **2 model runs** (Snowbun, Waddles), and the Figma **Starter plan has an MCP tool-call cap** that stopped image generation and downloads halfway through Sunny Beach. **Rule:** before a build, check the Figma and Weave plans can cover the whole job (about 40 concept images + retries, 40 Rodin runs at 36 credits, and one download call per image), and fetch each image in the same breath as generating it so a limit never strands paid art.
- **Rodin "8K Quad" is about 14,600 triangles**, not 8,000. `tools/node/optimize.mjs` (meshoptimizer simplify + 1024 px textures) takes any Rodin GLB under 7,500 triangles and still matches the concept side by side.
- **A pet block can fix drift without touching the style block:** Bloomhorn Stag got eyelashes; adding "plain solid black round button eyes, no eyelashes and no coloured rim" to its pet block fixed it in one retry.

## 2026-10-29 · First rules test (Bounce for Eggs)
Review of [[Game Design Rules]], then a test prototype (`prototype/bounce-for-eggs/index.html`: coins → hatch → pets add bounce → bounce pad to the next island) played by a playtest bot.

**From the review (before any code):**
- **A "recap when you leave" can't work in Roblox:** there is no UI while a player quits. **Rule:** the recap and gift go on the **return** ("welcome back"); every loop ends on a high instead.
- **The rarity example contradicted the budget:** 0.1% at 6 rolls/min is about 2.8 h, not weeks. **Rule:** the egg price sets the roll rate; price the top egg so one roll ≈ 1 min of play.
- **"Free gift after 10 minutes" broke "never reward staying longer".** **Rule:** playtime progress carries over between sessions.
- **16 hooks is too many for a first build** and fights the 5-item HUD cap. **Rule:** six MVP hooks first, the rest are later layers.

**From the playtest:**
- **The whole game was done in 20 seconds** (first pet 4.5 s, last island 19 s). **Rule:** the first upgrade has a floor too: 30-120 s of kid time.
- **A gate needed a 9% drop:** bounce counted each species once, so Cloud Hill needed the rare Fox; the bot needed 13 hatches. **Rule:** every gate is reachable with commons only; duplicates count; luck only makes you faster.
- **The island was empty most of the time:** the bot collected coins faster than they respawned (1 per 1.6 s). **Rule:** keep the world full; pace with prices, not scarcity.
- **Double-claim exploit:** the welcome-back gift was paid again on every quick reload, because the claim time was only saved every 5 s (coins went 1,900 → 5,022). **Rule:** stamp the claim in the same save as the grant (Roblox: one `UpdateAsync`). Test rejoin twice in a row.
- **Reset didn't wipe:** save-on-leave wrote the old save back after it was deleted. **Rule:** block saving while wiping.
- **The Hatch prompt slid under the Index tile.** **Rule (added to [[UI Rules]]):** world prompts are pushed clear of HUD items.
- **During the hatch show the player stood between the camera and the pet.** **Rule:** the show camera looks at the egg from the far side, so the player stands behind it watching; pickups hide during the show.
- **Every pet was the same round body** ("Sun Phoenix" looked like a cat). Fine for a test, not for a game. **Rule:** every collectible looks like its name.
- **What worked:** the 10-second first reward (coins right at spawn), the green arrow (coin → egg → pad), the odds chips at the egg, the index silhouettes with "1 / 4" page counts, the launch arc to the next island (a clip moment), the "Need 3 more bounce" bounce-in-place for a locked pad, rarity-scaled reveal with letter slam, phone landscape layout (844×390).
- **Tooling:** a playtest bot + timer panel turned "feels too fast" into numbers in minutes. **Rule:** every prototype gets both ([[Game Design Rules]] › 12). Kid time is estimated as bot time × 2.5 until a real kid plays.
- **Tooling:** Windows PowerShell 5.1 `Get-Content -Raw` reads UTF-8 files as ANSI, so a regex rewrite turned "·" into "Â·" and added a BOM. **Rule:** edit files with the Edit tool or Bash `sed`, not PowerShell read/write.
- **Tooling:** the browser pane pauses the game when it's hidden, so screenshots go stale and the clock stops. **Rule:** bring the tab to the front before timing or screenshots.
- **Tooling:** no Python or Node on this machine. A PowerShell static server lives in `.claude/serve.ps1` (launch config "prototypes", port 8771).

## 2026-10-29 · Game design chapter started
- **The rulebook had UI and page art, but no game design rules.** Earlier games were "not bad but not good", and that is mostly a design problem, not a UI one. **Rule:** every game starts with the pitch card in [[Game Design Rules]] (verb + reward name, 3-step chain, felt upgrade, rare chase, friend twist, clip moment, weekly drop) before any prototype code.
- **Obsidian MCP `obsidian_get_recent_changes` fails** with "Error 40012: Unknown or invalid Content-Type". Workaround: list the folder with `obsidian_list_files_in_dir` and read the notes.

## 2026-10-29 · Style round 3 (painted icon set)
- **Blender icons were still "low poly"** next to the user's painted reference (wood grain, satin, metal). Cause: simple 3D shapes can't produce painted detail. **Rule:** icons are AI-painted from one fixed style prompt (see [[UI Rules]] › Icons). The user's verdict: "much much much much better".
- **The gear's hole stayed white.** Cause: the background flood fill only reaches pixels connected to the image border. A global "clear every big white area" fix then ate the egg's shell and the white dots. **Rule:** clear enclosed holes one by one, seeded at that hole, never with a global threshold. Check every icon on the sky-blue background after cleanup.
- **The generated sizes varied** (the dots were tiny, the coin was huge). **Rule:** trim each icon and center it at 80% of a 1024 px square before adding the outline, so all icons fill their tiles the same way.
- **A drawn CSS coin sat next to the painted coin** on the price tags. **Rule:** one coin image everywhere: the counter, the flying coins and the price tags.
- **The user wants it perfect, and tweaking is welcome.** Keep refining after a "yes".

## 2026-10-29 · Style round 2 (icons rebuilt in Blender)
- **The user said the icons "look shit".** Cause: they were assembled live from raw blocks, spheres and cylinders, with flat toon shading and no bevels, highlights or shared light, so they read as programmer art. **Rule (later replaced in round 3):** UI icons are real renders, modeled in Blender with beveled edges, glossy coat, a warm key light from the top-left plus a rim light, and one thick even 2D outline added after rendering. Source: `prototype/starter-kit/icons/icon-studio.blend` (IconStudio scene, helpers in the `icon_lib.py` text block).
- **First renders came out muddy and grey** (whites read as grey, cream as beige). **Rule:** view transform Standard, key light about 1150 W, fill about 420 W, world 0.55. Check every set side by side on the sky-blue game background before using it.
- **Freestyle inner lines came out lavender.** Cause: the line color was entered as sRGB, but Blender expects linear values. **Rule:** convert UI hex colors to linear before putting them into Blender.
- **Highlight blobs got outlined and looked like eyes**, and a "liquid band" read as a belt. **Rule:** every added part has to read as part of the object at 48 px.
- **Icon motion is a 2D tween** (wiggle, pop) on the image, not a 3D spin. It matches what TweenService does on an ImageLabel, so the port is 1:1.
- **Toggle knob was off-center.** **Rule:** center knobs with top:50% plus translateY(-50%), and size them from the track's inner height.
- **The user's direction:** the purple UI in the TikTok clip was only a reference. Make our own style, and don't copy reference looks.

## 2026-10-29 · Style round 1 self-check (Chunky Pop demo)
- **Pop-up texts landed on top of the menu tiles** ("+25", "Need 280 more"). Cause: they were anchored above the coin counter, and the tiles sit directly above it. **Rule:** gain text appears beside the coin counter; error text appears at the button that was tapped, never in a HUD zone.
- **Tile grid sat too high on tablets.** Cause: it was centered in the free band, not on the screen. **Rule:** center the grid on the screen's middle, and only push it when it would hit the top bar or the coins.
- **Popups looked tiny on PC.** **Rule:** popups, prompts and effects use a per-device UI scale (phone 1, tablet 1.2, PC 1.35) set in Config.
- **Popups barely fit on a small phone** (390 pt tall once the top bar and home bar are reserved). **Rule:** no filler sentences in popups. Keep popup content to about 270 pt tall on phone, or it scrolls.

## 2026-10-29 · Feedback before the restart
- **Systems overwrote each other** in earlier games. **Rule:** one owner per thing (camera, HUD, coins, ...). Other systems ask the owner. Modules start in two passes: Init, then Start.
- **The UI overlapped badly on phones.** **Rule:** every HUD element goes through the Screen module, stays inside the safe area, keeps clear of Roblox's own controls, and passes the automatic overlap check at phone, tablet and PC sizes.
- **Too much UI = no good.** **Rule:** at most 5 HUD items. Today's layout uses 2: the tile grid (center-left, up to 6 tiles, only as many as needed) and the coins (bottom-left, above the thumbstick).
- **No HUD action button.** Open, talk and buy prompts sit on the objects in the world.
- **Popups:** centered horizontally, a little above the vertical middle, one at a time.


## 2026-10-29 — Game page art
- **Hit thumbnails are AI-painted, not Studio captures.** I first read the user's reference (avatar steals an egg from a sleeping dragon) as real renders with painted effects; the user spotted it is one AI image in the same glossy style as our UI icons. Lesson: check a reference for AI tells (even glossy shading, fused glows, a render too clean for Studio) before deciding how it was made.
- **Obsidian MCP `obsidian_patch_content` fails** with "Error 40084 ... requires an explicit 'Markdown-Patch-Version' header" (plugin API changed). Workaround: rewrite the whole note with `obsidian_put_content`, or append.
- **Glossy AI render looked "too AI-ish"** to the user. Fix that worked: prompt for "an unedited in-game screenshot from a Roblox experience, Future lighting", matte SmoothPlastic, flat 2D classic face decal, real sun shadows, plain sky with clouds, blocky terrain, and explicitly *no* glossy toy look, sparkles, bloom, rim light, depth-of-field or color grading. Only the reward glows (Neon). Our flat story marks still sit on top.
- **But the user preferred the punchy glossy look** over the fully natural screenshot ("first is better ... tweak it"). The middle ground: keep the glossy render style and close crop, but use SmoothPlastic with a soft satin sheen (not wet gloss), real cast shadows, a studded baseplate, a few blocky trees far back, and *no* painted swirl strokes, lens flare or heavy bloom; sparkles only on the reward.
- **Final page-art style = the 1st glossy test merged with the tweaked one** (user's call): semi-gloss (not wet) plastic, rim light, strong sparkle on the reward, patterned props and sky twinkles from the glossy one; real shadows, clouds, blocky trees, no swirls/flare/bloom from the tweaked one. The prompt is in [[Game Page Art]]. 5 generations used to get there.

## 2026-10-08 to 10-22 · Boo Town look back (the earlier game)
Written 2026-10-29 from Boo Town's QA rounds (`prototype/boo-town/qa/`, final QA 21 Oct: NO-GO) and the owner questions. It sits at the bottom because it is the oldest. Boo Town is why the rulebook exists: "not bad but not good".

- **Feature pile-up.** New systems kept landing (action combat in every boss, Costume Contest, Team BOO, rebirth, Fresh Houses, Gold pets, 42 colour swatches) while the last NO-GO list was still open. The combat layer was never even logged. **Rule:** one feature at a time through the whole pipeline; no new layer before QA says GO ([[QA Rules]] › 1).
- **Too many currencies:** Candy, Spook Points, Gold, Prize Tickets, plus potions, streaks, coffin meters and pet copies on screen. **Rule:** one currency ([[Game Design Rules]]); the HUD cap of 5 ([[UI Rules]]).
- **Bosses too hard for a young solo player:** all 3 hearts gone in ~5.5 s standing still, ~150 hits per boss, and losing reset the boss to full health. **Rule:** failure keeps the progress you made (checkpoints); a solo kid finishes the first boss in under ~8 min (bot-timed).
- **Social features nobody could test:** the contest needed 3+ players, Team BOO 2-4, and no 2-player Start Server was ever run. **Rule:** every social feature works on a near-empty server (NPC stand-ins) and gets a real 2-player test.
- **Halloween-only theme:** seasonal games drop on 1 November, and the plan to fix it came 10 days before launch. **Rule:** pick a theme that lasts all year; seasons are overlays on top.
- **A six-pointed star in the coffin show's floor circle.** **Rule:** check every symbol and emblem ([[QA Rules]] › 3).
- **Emotes only on the G key:** no button on phone, tablet or gamepad. **Rule:** every action on every input.
- **Threatening boss lines** ("Everything BURNS!") and a **score window with minus numbers and zeros.** **Rule:** no threats, never show a child a minus or a "you got nothing".
- **Boss pet odds 1 in 50** (~95 wins for both pets of a boss). **Rule:** the grind budget in [[Game Design Rules]] › 3 sets the odds.
- **Launch blocked on owner-only items:** all Robux product, pass and badge ids were 0. **Rule:** list owner items early, not at the final QA.
- **Code:** a quick rejoin on the same server could load a stale save; boss steps trusted the position the client claimed. **Rule:** in [[Code Rules]] › 6-7 and [[QA Rules]] › 6.
- **What worked:** server rule test suites (PetRules 220 checks, BossRules 207), dev commands for rare paths (`coffinPity`, `petGrant`), a separate QA save key, a three-reviewer QA (play-tester, code audit, design review) with ids and repro steps, an exploit retry script, an owner-questions table so work never waited on an answer, and the pet hatch / coffin shows. These became [[QA Rules]] and [[Animation Rules]] › 3.


## 2026-10-29 · Vault reminder hook + Windows tooling
- **What:** a Claude Code Stop hook (`~/.claude/hooks/vault-reminder.ps1`, set in `~/.claude/settings.json`) now asks once, after any turn that edited files / Studio / Figma / Blender and did not write to the vault, whether there is a lesson or rule change to log here. It never loops (skips when `stop_hook_active`). Delete the `hooks` → `Stop` entry to switch it off.
- **Lesson:** this PC has no `jq` or `node`, and `python` is only the Microsoft Store stub. Write hook and helper scripts in PowerShell (`powershell.exe -NoProfile -ExecutionPolicy Bypass -File ...`), not bash + jq or Python.

## 2026-10-29 · First pets (Ice Ray for Pets, Frostfox)
- **The first painted pet "looked strange".** Realistic fur strands, anime eyes with eyelashes, and a pale sky-blue instead of the asked-for deep teal (it would vanish in the light-blue ice cube). The model ignored "satin vinyl". **Rule ([[Pet Rules]] › 9):** say "deep, rich, saturated", "simple round black eyes with one white shine dot, no eyelashes", and name the finish you want.
- **A style test in one image works.** The same pet in three styles side by side (glossy vinyl, soft clay, painted with outline) cost one generation and gave the owner a real choice. They picked **soft clay**. **Rule ([[Pet Rules]] › 5):** every game starts its pets with this style test, then locks the style block.
- **Hand-built Blender pets were rejected outright** ("looks very shit and nothing like the photo"). Spheres and cones make a balloon toy, never the concept. Third time simple 3D shapes lost to painted detail (after the icon rounds). **Rule:** pets go to 3D only through image-to-3D from the approved concept, judged side by side with it.
- **Weave Rodin V2 matched the concept closely** (36 Weave credits, about 2 min, textured GLB, 19,810 triangles at the 20K setting). Glowing parts come out painted, not glowing, so they need Neon or a light in Roblox. Method in [[Games/Ice Ray for Pets/Pet Art Recipe]] › 9.
- **Tooling:** Weave needs the Figma account linked at app.weavy.ai settings; the first tries after linking still said "not linked" for a while. `weave_upload_asset`'s picker doesn't show in Claude Code: POST the file as multipart `file=` to the returned `submitUrl` with `Authorization: Bearer <token>` (the token as a form field is refused). Blender MCP's generators were all off and the addon out of date. No Python on this PC: crop images with PowerShell `System.Drawing`.
- **Owner direction:** pets first, rules after; the whole game should be buildable by a friend from one prompt ([[Games/Ice Ray for Pets/Build Prompt]]); 8 pets per zone stays.
