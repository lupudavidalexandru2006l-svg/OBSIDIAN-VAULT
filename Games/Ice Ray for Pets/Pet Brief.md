---
created: 2026-10-29
tags: [game, pets, brief]
status: brief, roster not designed yet
---

# Ice Ray for Pets: Pet Brief

What this game needs from its pets. The process and quality bar are in [[Roblox Setup/Pet Rules]]; the game is in [[Games/Ice Ray for Pets/Game Plan]]. **Pets are made first.**

## 1. How many
> [!note] Owner decision 2026-10-29: a Secret in every zone
> The Game Plan (section 5) said Secrets only in zones 4-5; this brief gave every zone one. The owner first picked zones 4-5, then changed it to **a Secret in every zone** (1 in 20,000). The Game Plan now matches this brief.

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

### Status
- **2026-10-29:** all 8 Meadow concepts made and **approved by the owner** (line-up: `pets/snowy-meadow-lineup-v1.png`). Files and log in [[Games/Ice Ray for Pets/Pet Art Recipe]] › 6-7.

## 11. The other zones (drafted 2026-10-29)
Designed the same way as the Meadow, from section 2's themes: 2 Common, 1 Uncommon, 1 Rare, 1 Epic, 1 Legendary, 1 Mythic, 1 Secret per zone, a different main colour and silhouette for every pet in its zone, rarity extras from [[Games/Ice Ray for Pets/Pet Art Recipe]] › 4. Cold to hot: Forest keeps earthy woodland colours, Beach goes bright, Desert and Volcano go warm (heat contrast, section 3). Every prompt below is a **pet block**: paste it after the locked style block, like the Meadow ones.

**Symbols checked:** no crosses, crescents, stars of David, halos, hieroglyphs, ankhs or eye symbols; emblems are a leaf (Bloomhorn Stag) and a sun gem (Solaris Sphinx). **One exception to heat contrast:** Lavalamp Jelly (Volcano Secret) is cool indigo on purpose so its warm glowing blobs pop; owner can change it.

### 11.1 Pine Forest (zone 2): woodland, pinecones, moss, mushrooms, lanterns
| Tier | Name | Species / rig | Main colour | Silhouette hook | Signature move | Size |
|---|---|---|---|---|---|---|
| Common | **Conehog** | hedgehog / Quadruped | chestnut brown | its whole back is one big pinecone of chunky scales | curls into a pinecone ball and rolls a little loop | S |
| Common | **Hopsprout** | frog / Quadruped | honey gold | a two-leaf green sprout on top of its head | a big hop, the sprout's leaves flap like wings on the way down | S |
| Uncommon | **Capmouse** | mouse / Quadruped | plum purple | oversized red mushroom cap with white spots as a hat | hides under its cap, then pops out | S |
| Rare | **Mossfawn** | deer fawn / Quadruped | deep forest green | moss patches with tiny white flowers along its back, white fawn spots | shakes, and flowers pop open along its back | M |
| Epic | **Lanternbug** | firefly / Bird | deep indigo | round glowing amber lantern for a back end, curly antennae | blinks its lantern three times; tiny lights blink back around it | S |
| Legendary | **Mapleguard Bear** | bear cub / Quadruped | crimson red | carved wooden armour plates + crown of branches with orange maple leaves, falling-leaf aura | stomps, and a whirl of maple leaves spins around it | L |
| Mythic | **Bloomhorn Stag** | stag / Custom (floats) | deep magenta | glowing blossom antlers, glowing hooves, leaf emblem, petal-and-mote trail | rears up and a ring of blossoms blooms on the ground | M |
| Secret | **Glowshroom Mammoth** | mammoth calf / Custom | midnight teal | a tiny forest of glowing cyan mushrooms on its back, curly vines instead of tusks | shakes its back and glowing spores drift up like fireflies | M |

- **Conehog:** The pet: Conehog, a baby hedgehog. Chestnut brown with a cream face and tummy. Its whole back is one big rounded pinecone made of chunky overlapping clay scales instead of spines. Simplest and cutest, no accessories.
- **Hopsprout:** The pet: Hopsprout, a baby frog. Honey gold with a cream belly and round toe pads. A little green two-leaf sprout grows from the top of its head like a tiny plant. Simplest and cutest, no accessories.
- **Capmouse:** The pet: Capmouse, a baby mouse. Plum purple fur with a cream tummy and big round ears. It wears an oversized red mushroom cap with white spots as a hat, and has a long thin curly tail.
- **Mossfawn:** The pet: Mossfawn, a baby deer fawn. Deep forest green with white fawn spots on its back and a cream chest. Soft patches of moss with tiny white flowers grow along its back and on top of its head like a cap, and two tiny rounded antler nubs.
- **Lanternbug:** The pet: Lanternbug, a baby firefly. Deep indigo round body with chunky round wings in a lighter violet and two short curly antennae. Its round back end is a glowing warm amber lantern with a small soft glow.
- **Mapleguard Bear:** The pet: Mapleguard Bear, a baby bear cub sitting up. Deep crimson red fur in chunky clumps with a cream muzzle and belly. It wears smooth carved wooden armour plates on its shoulders and back, and a crown of curling branches with bright orange maple leaves on its head, with a soft aura of falling maple leaves around it.
- **Bloomhorn Stag:** The pet: Bloomhorn Stag, a baby stag floating in the air with its legs tucked. Deep magenta pink fur in chunky clumps with a cream chest. Its antlers are branches covered in glowing pink and white blossoms, its hooves glow soft white, and a glowing leaf emblem sits on its chest, with a trail of tiny glowing petals and light motes behind it. Several glowing neon parts and a soft magical aura.
- **Glowshroom Mammoth:** The pet: Glowshroom Mammoth, a baby woolly mammoth. Midnight teal shaggy wool in big chunky clumps, a cream face, and soft curling green vines instead of tusks. A little forest of glowing cyan mushrooms of different sizes grows on its back, lighting it from above, with tiny glowing spores floating around. The strangest and coolest pet of the zone.

### 11.2 Sunny Beach (zone 3): sea and sun, shells, floaties, sunglasses
| Tier | Name | Species / rig | Main colour | Silhouette hook | Signature move | Size |
|---|---|---|---|---|---|---|
| Common | **Puffsy** | pufferfish / Swimmer | tangerine orange | a perfect ball with soft round bumps, tiny fins | puffs up to double size, then deflates with a little toot | S |
| Common | **Starbit** | starfish / Blob | hot magenta | five chunky arms, standing on two of them | cartwheels across the sand | S |
| Uncommon | **Flopseal** | seal pup / Swimmer | deep cobalt blue | yellow-and-white striped swim ring round its middle | belly-flops and bounces on its floatie | M |
| Rare | **Pearlsnail** | snail / Blob | sunny yellow | big spiral shell with pearly pink and gold stripes | hides in its shell and spins like a top | S |
| Epic | **Glowfin** | dolphin calf / Swimmer | deep sea green | glowing white pearl on its forehead | leaps in an arc and splashes a little rainbow | M |
| Legendary | **Reefback Turtle** | sea turtle / Swimmer | coral red | a tall coral-reef shell with branching spires and anemones, bubble aura | pulls in, then the reef on its back sways and puffs bubbles | L |
| Mythic | **Prismapus** | octopus / Custom (floats) | deep orchid purple | eight curling tentacles with rainbow-glowing tips, rainbow gem, bubble trail | spins and paints a rainbow ring in the air | M |
| Secret | **Beacon Orca** | orca calf / Swimmer (floats) | jet black + white patches | a tiny striped lighthouse on its head with a glowing lamp | the lighthouse beam sweeps a full circle across the server | M |

- **Puffsy:** The pet: Puffsy, a baby pufferfish. Tangerine orange with a cream belly. A perfectly round ball-shaped body covered in soft rounded clay bumps, tiny fins and a small fan tail, floating just above the ground. Simplest and cutest, no accessories.
- **Starbit:** The pet: Starbit, a baby starfish standing upright on two of its five arms. Hot magenta pink with soft cream dots. Five chunky rounded arms with its face in the middle. Simplest and cutest, no accessories.
- **Flopseal:** The pet: Flopseal, a baby seal pup. Deep cobalt blue with a white muzzle and belly and short whiskers. It wears a yellow-and-white striped swim ring floatie around its middle.
- **Pearlsnail:** The pet: Pearlsnail, a baby snail. Sunny yellow soft body with two short round feelers on top of its head. Its big spiral shell has a pearly pattern of pink and gold stripes with a soft shine.
- **Glowfin:** The pet: Glowfin, a baby dolphin. Deep sea green with a white belly, a round smiling face and a short rounded beak. A glowing white pearl sits on its forehead with a small soft glow.
- **Reefback Turtle:** The pet: Reefback Turtle, a baby sea turtle. Coral red skin with cream flippers. Its shell is a tall elaborate coral reef with branching coral spires in orange and pink, little round anemones and a few small seashells, with a soft aura of tiny bubbles around it.
- **Prismapus:** The pet: Prismapus, a baby octopus floating in the air. Deep orchid purple with a cream face patch. Eight short chunky curling tentacles whose tips glow in rainbow colours, a glowing rainbow gem on its forehead, and a trail of glowing bubbles and light motes behind it. Several glowing neon parts and a soft magical aura.
- **Beacon Orca:** The pet: Beacon Orca, a baby orca floating as if swimming through the air. Jet black with bold white belly and eye patches; its eyes are the same round black eyes with a white shine dot, set in the white patches. On top of its head stands a tiny striped red-and-white lighthouse with a glowing lamp that shines a soft beam of light, with water sparkles around it. The strangest and coolest pet of the zone.

### 11.3 Desert Dunes (zone 4): cactus, sand, gems, sunsets, ancient-toy look
| Tier | Name | Species / rig | Main colour | Silhouette hook | Signature move | Size |
|---|---|---|---|---|---|---|
| Common | **Catcus** | kitten / Quadruped | cactus green | a round cactus-shaped kitten with soft nubs instead of spines | a pink flower pops open on its head | S |
| Common | **Fenny** | fennec fox / Quadruped | sunset orange | giant ears twice as tall as its head | ears turn like radar, then it pounces | S |
| Uncommon | **Lumpkin** | camel calf / Quadruped | chocolate brown | one big hump with a woven turquoise-and-gold tasselled blanket | sits down in a puff of sand with a big smile | M |
| Rare | **Scarabit** | beetle / Custom | royal purple | round dome shell with a turquoise-and-gold mosaic | rolls a ball of sand bigger than itself | S |
| Epic | **Sunfrill** | frilled lizard / Quadruped | crimson red | a big round neck frill that glows warm gold | flares its frill open like a sunrise | M |
| Legendary | **Dunehorn Ram** | ram lamb / Quadruped | deep rose pink | huge curled gold horns with turquoise gems, sandstone shoulder plates, sand-swirl aura | headbutt-hop, and a ring of golden sand swirls out | L |
| Mythic | **Solaris Sphinx** | winged cat / Custom (floats) | rich gold | glowing turquoise feather wings, sun gem on its forehead, sparkle trail | spreads its wings and the sky behind it turns sunset-gold | M |
| Secret | **Mirage Manta** | manta ray / Swimmer (floats) | deep turquoise teal | a tiny oasis with a pool and a palm tree on its back | dives into the sand and surfaces somewhere else in a shimmer | M |

- **Catcus:** The pet: Catcus, a baby kitten shaped like a round cactus. Cactus green with a cream muzzle, and soft round clay nubs dotted over its body instead of spines. Pointed cat ears and a short stubby tail. Simplest and cutest, no accessories.
- **Fenny:** The pet: Fenny, a baby fennec fox. Sunset orange with a cream face, chest and inner ears. Giant ears twice as tall as its head, standing straight up. Simplest and cutest, no accessories.
- **Lumpkin:** The pet: Lumpkin, a baby camel. Chocolate brown with a cream muzzle, knobbly knees and one big round hump. Over its hump it wears a woven saddle blanket in turquoise and gold with little tassels.
- **Scarabit:** The pet: Scarabit, a baby beetle. Royal purple with a big round dome shell covered in a shiny mosaic pattern of turquoise and gold tiles, six short stubby legs and two little round feelers.
- **Sunfrill:** The pet: Sunfrill, a baby frilled lizard. Crimson red with a cream belly and a long curling tail. Around its neck is a big round frill like a collar that glows warm gold with a small soft glow.
- **Dunehorn Ram:** The pet: Dunehorn Ram, a baby ram lamb. Deep rose pink wool in big chunky clumps with a cream face. Huge curled gold horns set with turquoise gems, smooth sandstone armour plates on its shoulders, and a soft aura of swirling golden sand around it.
- **Solaris Sphinx:** The pet: Solaris Sphinx, a baby winged cat floating in the air. Rich gold fur in chunky clumps with a cream muzzle. Wings of glowing turquoise feathers, a glowing sun gem on its forehead, a glowing turquoise tail tip, and a trail of golden sparkles and light motes behind it. Several glowing neon parts and a soft magical aura.
- **Mirage Manta:** The pet: Mirage Manta, a baby manta ray gliding through the air. Deep turquoise teal with a cream underside and a glowing gold pattern of dots along its wings. On its back sits a tiny oasis with a little pool of water and one palm tree, with shimmering heat sparkles trailing behind it. The strangest and coolest pet of the zone.

### 11.4 Volcano (zone 5): lava, obsidian, embers, crystals, friendly
| Tier | Name | Species / rig | Main colour | Silhouette hook | Signature move | Size |
|---|---|---|---|---|---|---|
| Common | **Emberpup** | puppy / Quadruped | tangerine orange | its tail is a rounded flame shape | chases its flame tail in a circle | S |
| Common | **Magmallow** | lava slime / Blob | raspberry red | a gumdrop blob with a toasted marshmallow cap melting over its top | squashes flat, then boings up | S |
| Uncommon | **Obby** | rhino calf / Quadruped | obsidian black | one short round horn + chunky orange goggles on its forehead | charges three steps and skids to a stop | M |
| Rare | **Sizzlemander** | salamander / Quadruped | lime green | big round black spots, long curling tail, little smoke puffs | sizzles, and smoke rings float up | S |
| Epic | **Flarechick** | phoenix chick / Bird | hot magenta | a flame-shaped crest that glows orange and gold | flaps, and its crest flares into a big flame | S |
| Legendary | **Geodillo** | armadillo / Quadruped | royal purple | back plates that are split-open geodes of glowing crystals, crystal crown, ember aura | rolls into a crystal ball and spins | L |
| Mythic | **Pyrokoi** | koi fish / Swimmer (floats) | molten gold | long fins and tail of glowing lava ribbons, ember trail | swims a loop and leaves a ring of embers | M |
| Secret | **Lavalamp Jelly** | jellyfish / Blob (floats) | cobalt indigo | a glassy bell with glowing lava-lamp blobs drifting inside | its blobs rise and pop into sparkles over everyone | M |

- **Emberpup:** The pet: Emberpup, a baby puppy. Tangerine orange with a cream muzzle and chest and round floppy ears. Its tail is a rounded clay flame shape in orange and yellow, solid and not glowing. Simplest and cutest, no accessories.
- **Magmallow:** The pet: Magmallow, a baby lava slime. A soft round raspberry red blob shaped like a gumdrop, with a cream face and a toasted marshmallow cap melting over its top. Simplest and cutest, no accessories.
- **Obby:** The pet: Obby, a baby rhino. Obsidian black skin in chunky smooth plates with a warm grey face and belly and one short rounded horn. It wears chunky orange safety goggles pushed up on its forehead.
- **Sizzlemander:** The pet: Sizzlemander, a baby salamander. Lime green with big round black spots all over its back, a cream belly and a long curling tail, with little round clay smoke puffs rising from its back.
- **Flarechick:** The pet: Flarechick, a baby phoenix chick. Hot magenta pink round fluffy body with a cream belly, a small orange beak and tiny wings. On top of its head is a crest shaped like a flame that glows bright orange and gold, with a small soft glow.
- **Geodillo:** The pet: Geodillo, a baby armadillo. Royal purple with a cream face and belly. Its back is covered in big armour plates that are split-open geodes full of glowing amethyst and orange crystals, with a small crown of crystals on its head and a soft aura of drifting embers around it.
- **Pyrokoi:** The pet: Pyrokoi, a baby koi fish floating in the air. Molten gold body in chunky smooth scales with a cream belly. Its long flowing fins and tail are ribbons of glowing lava orange and red that fade to light at the tips, with a trail of glowing embers and light motes behind it. Several glowing neon parts and a soft magical aura.
- **Lavalamp Jelly:** The pet: Lavalamp Jelly, a baby jellyfish floating in the air. A deep cobalt indigo glassy bell with a cute face on the front and short chunky curling tentacles. Inside the bell, big soft glowing orange and pink blobs float slowly like a lava lamp, with a soft warm glow and sparkles around it. The strangest and coolest pet of the zone.

### Status of the other zones
- **2026-10-29:** rosters and prompts drafted by the builder. The owner said to carry on without stopping, so concepts follow zone by zone (one pet first per zone).
