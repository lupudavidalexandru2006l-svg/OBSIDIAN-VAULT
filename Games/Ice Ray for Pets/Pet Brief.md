---
created: 2026-10-29
tags: [game, pets, brief]
status: brief, roster not designed yet
---

# Ice Ray for Pets: Pet Brief

What this game needs from its pets. The process and quality bar are in [[Roblox Setup/Pet Rules]]; the game is in [[Games/Ice Ray for Pets/Game Plan]]. **Pets are made first.**

## 1. How many
> [!warning] Owner decision 2026-10-29: Secrets only in zones 4-5
> The Game Plan (section 5) and this brief disagreed. The owner chose the Game Plan: **Secret pets spawn only in Desert Dunes and Volcano** (1 in 20,000). The Secret lines below and Snowglobe Drake (section 10) need updating once the owner says where those pets go.

- **Launch:** 5 zones × 7 regular pets = **35**, plus **1 Secret per zone = 5**. Total 40.
- Per zone: 2 Common, 1 Uncommon, 1 Rare, 1 Epic, 1 Legendary, 1 Mythic (+ the Secret).
- **Hybrids:** about 6 per zone (30 at launch), each a pair from the same zone.
- **Weekly drops after launch:** Candy Glacier (7 + 1 Secret), the Heat Wave boss reward pet, and a few seasonal pets (section 7).

## 2. Zone families
| # | Zone | Theme for the family | Accent materials | Example ideas (placeholders) |
|---|---|---|---|---|
| 1 | Snowy Meadow | fluffy winter animals, mittens, scarves, earmuffs | snow, wool, knit | Snowbun (bunny), Pupcicle (puppy), Mittenkit (cat), Waddles (penguin), Frostfox (fox), Yeti Jr (little yeti), Aurora Owl (mythic, aurora wings) |
| 2 | Pine Forest | woodland, pinecones, moss, mushrooms, lanterns | wood, moss, bark | pinecone hedgehog, moss deer, acorn squirrel, lantern firefly, bark bear, a forest-spirit stag (mythic) |
| 3 | Sunny Beach | sea and sun, shells, floaties, sunglasses | shell, sand, coral, glass | crab with a shell hat, seal with a floatie, dolphin, starfish blob, coral turtle, a rainbow kraken (mythic, friendly) |
| 4 | Desert Dunes | cactus, sand, gems, sunsets, ancient-toy look | sandstone, cactus, turquoise, gold | cactus cat, sand fennec, camel pup, gem scarab, sun-lizard, a golden sphinx-cat (mythic) |
| 5 | Volcano | lava, obsidian, embers, crystals (friendly, never scary) | obsidian, glowing magma, crystal | ember pup, magma slime, obsidian rhino, fire salamander, phoenix chick, a lava dragon (mythic) |

The names and ideas are placeholders: the pet session designs the real roster from the Pet Rules. Each Secret is the strangest and coolest pet of its zone.

## 3. Game-specific needs (on top of Pet Rules)
- **Freeze poses.** Every pet needs **five readable poses** that it loops through in the wild and keeps when frozen: **idle, yawn, jump, dance, sneeze** (sneeze is rare and the funniest). Each pose must read as a still frame inside an ice cube. Shared per rig family, with special versions for Mythics and Secrets.
- **Asleep pose** for night time (pets sleep and are easy to freeze).
- **Dazed pose** for when a cube melts (stars or snowflakes circling the head, never hurt).
- **Thaw pop-out** for when the cube cracks open in the pen: a happy burst, then the signature move.
- **Readable in the ice cube.** The cube is light blue and mostly clear; the pet's main color and silhouette must read through it. Check every pet in a cube at 30 studs on a phone, at every melt stage.
- **Carried on the player's back** in a cube: it must not hide the player's head or block the camera.
- **Cube size follows size class** (S, M, L, Giant).
- **Heat contrast:** cold-zone pets are fluffy and cool-colored; hot-zone pets are warm-colored, so a Volcano pet in a melting cube looks great.

## 4. Mutations in this game
Golden, Rainbow, Frosty (Big Chill), Night, Lava (Volcano only), Giant. Looks per [[Roblox Setup/Pet Rules]] › 7. Pose bonus is separate from mutations (Normal, Yawn, Jump, Dance, Mid-Sneeze).

## 5. Crate-only cosmetic variants
Frozen Crates hold the same pets as the wild, plus **cosmetic variants** you can only get from crates (no stat bonus): for example **Crystal**, **Candy** and **Galaxy** skins. Each variant is a material/color swap on the same model, designed for the whole zone at once.

## 6. Order of work
1. **Snowy Meadow first, as the style test:** pet cards → concepts → line-up → the user approves → model the first two with each 3D method → pick the method → finish the family.
2. The Meadow pets go into the prototype, replacing the stand-ins.
3. Then Pine Forest, Sunny Beach, Desert Dunes, Volcano, each as a family.
4. Hybrids per zone after that zone's pets are approved.
5. Crate variants last.

## 7. After launch
| Drop | Pets |
|---|---|
| Week 1, Heat Wave boss | Sunny the sun-blob (boss reward, blob rig) |
| Week 3, Candy Glacier | 7 candy-ice pets + 1 Secret |
| Seasonal (winter, summer, Halloween candy-bright) | 3-4 themed pets each, never scary |

## 8. Done means
Every pet passes the [[Roblox Setup/Pet Rules]] checklist, plus section 3 here (5 poses, asleep, dazed, thaw, readable in the cube).

## 9. How the pet pictures are made
Step-by-step recipe (tool, model, prompt, file names, checks), written so the person building the game can make every pet the same way: [[Games/Ice Ray for Pets/Pet Art Recipe]].

## 10. Snowy Meadow roster (agreed 2026-10-29)
8 pets per zone stays (owner's decision). **Frostfox is the only pet with finished art** (`frostfox-clay-v1.png` concept + `frostfox-3d-rodin-v1.glb` 3D model) and is the style reference. The other 7 have cards and ready-to-use prompts below but **no art yet**. Make them with [[Games/Ice Ray for Pets/Pet Art Recipe]].

| Tier | Name | Species / rig | Main colour | Silhouette hook | Signature move | Size |
|---|---|---|---|---|---|---|
| Common | **Snowbun** | bunny / Quadruped | bubblegum pink | giant floppy ears that wrap round its head like earmuffs, pom-pom tips | "ear-copter": spins its ears and floats down | S |
| Common | **Waddles** | penguin / Biped | midnight navy (yellow beak and feet) | bowling-pin body + very long red-and-white striped scarf trailing behind | belly-slide toboggan | S |
| Uncommon | **Mittenkit** | kitten / Quadruped | sunny orange | knit bobble hat with a big pom-pom, knit mittens, question-mark tail | catches a snowflake between its mittens and stares at it | S |
| Rare | **Pupcicle** | puppy / Quadruped | lemon yellow | ice-pop coat with frosting drips, popsicle-stick tail, one ear with a bite out | shakes like a wet dog, spraying sprinkles and snow | M |
| Epic | **Frostfox** | arctic fox / Quadruped | deep teal | tail bigger than its body ending in a glowing ice crystal, glowing forehead gem | tail swish that draws a glowing snowflake in the air | M |
| Legendary | **Blizzard Yeti** | young yeti / Biped | lavender purple | broad chunky shoulders with glowing ice shoulder plates, crown of ice crystals, snowflake aura | stomps, and a ring of frost bursts across the ground | L |
| Mythic | **Aurora Owl** | owl / Bird (floats) | aurora green (pink and violet ribbons) | wings made of glowing aurora ribbons, glowing snowflake emblem on its chest, light-mote trail | spreads its wings and an aurora curtain ripples across the sky | M |
| Secret | **Snowglobe Drake** | little dragon / Custom | ruby red (gold horns) | carries a glowing snow globe on its back like a shell, a tiny snowy village inside | shakes the globe and real snow bursts out over everyone | M |

Why these colours: the ice cube is light blue, so no main colour is pale blue or plain white, and all 8 are different. The chest emblem on Aurora Owl is a snowflake, not a crescent moon, to keep clear of religious symbols ([[Roblox Setup/Pet Rules]] › 3).

### Exact prompts (style block + pet block, paste as one prompt)
Every prompt starts with the **style block** from [[Games/Ice Ray for Pets/Pet Art Recipe]] › 3, word for word, then one of these pet blocks:

- **Snowbun:** The pet: Snowbun, a baby bunny. Bubblegum pink fur with a white tummy. Giant floppy ears that hang down and wrap around the sides of its head like fluffy earmuffs, each ear ending in a round white pom-pom. Simplest and cutest, no accessories.
- **Waddles:** The pet: Waddles, a baby penguin. Midnight navy body with a white belly, bright yellow beak and yellow feet. A tall rounded bowling-pin body with little flippers, and a very long red-and-white striped knit scarf wrapped once around its neck with both ends trailing behind it. Nothing else.
- **Mittenkit:** The pet: Mittenkit, a baby kitten. Sunny orange fur with a cream chest and muzzle. A red-and-cream knit bobble hat with a big round pom-pom on top, small matching knit mittens on its front paws, and its tail curled up like a question mark.
- **Pupcicle:** The pet: Pupcicle, a baby puppy. Lemon yellow with white accents. Its coat looks like a frozen ice pop, with thick smooth white frosting drips running down its back and a few rainbow sprinkles, one floppy ear with a small round bite missing, and its tail is a wooden popsicle stick.
- **Frostfox:** The pet: Frostfox, a baby arctic fox. Deep saturated teal fur with a white chest and white muzzle. A giant fluffy tail bigger than its body, curling up behind it, the tail tip is a glowing cyan ice crystal. A small glowing gem on its forehead.
- **Blizzard Yeti:** The pet: Blizzard Yeti, a baby yeti standing upright. Lavender purple shaggy fur in big chunky clumps, a pale lilac face and belly, big flat feet. Broad chunky shoulders with smooth glowing ice-crystal shoulder plates, a small crown of glowing ice crystals on its head, and a soft cold aura of tiny sparkling snowflakes around it.
- **Aurora Owl:** The pet: Aurora Owl, a baby owl floating in the air. Emerald aurora-green feathers in chunky clumps, a white face disc, two small feather tufts on its head, a glowing snowflake emblem on its chest. Its wings are spread open and made of glowing flowing aurora ribbons in green, pink and violet that fade to light at the tips, with a trail of tiny glowing light motes behind it. Several glowing neon parts and a soft magical aura.
- **Snowglobe Drake:** The pet: Snowglobe Drake, a baby dragon. Ruby red with small gold horns, a cream belly, small rounded wings and a short curled tail. On its back it carries a big clear glass snow globe like a turtle shell, with a tiny snowy village and pine trees inside and snow falling in it, the globe glowing softly from inside, a sparkle of magic around it. The strangest and coolest pet of the zone.

### What the other zones need
Pine Forest, Sunny Beach, Desert Dunes and Volcano still need their 8 pets designed: themes and placeholder ideas are in section 2. Design each zone the same way as the Meadow: cards first (different main colour and silhouette for every pet, the rarity ladder from Common to Secret), the owner approves the roster, then prompts and art.
