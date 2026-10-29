---
created: 2026-10-29
tags: [roblox, sound, audio, music, rules]
status: draft, not yet used on a ported game
---

# Sound Rules

How our games sound: button clicks, rewards, music, the world around you and the big shows. Related: [[Animation Rules]], [[UI Rules]], [[Code Rules]], [[Game Design Rules]] › 8 (living soundscape), [[Lessons]], [[Home]].

> [!summary] The short version
> **Every action makes a happy sound, the music never stops, and nothing is ever loud or startling.** Sounds mean things the same way colors do. Rarer = richer. And every sound has a visual partner, because many kids play with the sound off.

## 1. Principles
- **Every tap and every win makes a sound.** No silent buttons, no silent rewards.
- **Never loud, never startling.** No sudden blasts, screams, harsh buzzers or jump-scare stings. Sound effects stay quieter than a normal speaking voice next to the music.
- **Sound never carries information alone.** Every sound has a visual partner (pop, glow, shake), so a kid with a muted phone misses nothing.
- **All volumes, sound IDs and pitch ranges live in `Config.sounds`.** No IDs or volumes in game code.
- **One `Audio` module owns all sound** ([[Code Rules]] › One owner): music, volume groups, ducking. Other systems ask it to play a named sound (`Audio.play("coin")`), they never create `Sound` objects themselves.

## 2. Sounds mean things (like colors)
| Meaning | Sound | Color partner |
|---|---|---|
| **Yes / collect / go** | Bright, rising, short (pop, chime going up) | green |
| **Reward / coins** | Sparkly bell or coin clink, higher on a streak | yellow |
| **Not yet** (can't afford, locked) | Soft low "bonk" or boing, falling pitch. Friendly, never a buzzer | red shake |
| **Info / open menu** | Soft woody tap or whoosh | blue |
| **Close / back** | The open sound, lower | |
| **Rare / special** | A longer, richer chord that grows with rarity | the rarity color |

Keep each meaning to one sound family across the whole game.

## 3. Feel and juice
- **Streaks climb:** each pickup in a quick streak plays a little higher (Bounce for Eggs: +60 Hz per coin). The streak resets after a short pause (`Config.sounds.streakReset`, about 1.5 s).
- **Small random variation:** pitch ±5% (`PlaybackSpeed` 0.95-1.05) on repeated sounds, so the 500th coin doesn't grate.
- **Cap repeats:** at most a few copies of the same sound at once (`Config.sounds.maxSame`, about 3). Spam-clicking or a coin shower never becomes noise.
- **Button press:** a click on the press, nothing on release.
- **Sound and motion land together:** the sound starts on the frame the pop or press starts ([[Animation Rules]] › motion set).

## 4. Rarity scales the sound
| Rarity | Reveal sound |
|---|---|
| Common / Uncommon | one short happy pop + chime |
| Rare / Epic | a rising 3-4 note chime |
| Legendary | build-up + a bright fanfare |
| Mythic / Secret | the full show: heartbeat build-up, a big shimmer on the burst, a fanfare, and a chime others can hear nearby |

- Same honesty rule as the shows: **the build-up sound never hints at a better result** than the one you got.

## 5. Music
- **The music never stops** while playing: one gentle, cheerful loop per zone, crossfaded (about 1.5 s) when you change zone. Boo Town already does this with one song per area.
- **Music sits under the sound effects** (Boo Town's mix: music 0.55 × 0.32 under sound 0.8). Kids should hear their wins over it.
- **Shows duck the music** (down to about 30%) and bring it back after the OK button. The show asks `Audio` to duck; it never stops the music itself.
- **Loops have no hard seam and no loud peaks.** Listen to the loop point before using a track.
- **Keep it upbeat and simple:** bright instruments, a medium tempo. No dark, tense or "danger" music, even in boss areas: goofy-big, not scary.

## 6. The world (living soundscape)
- **Quiet ambient loops per zone:** birds, wind, water, a distant crowd. Much quieter than the music.
- **Things in the world sound where they are:** 3D `Sound`s inside the part, with `RollOffMaxDistance` set so a pickup is heard only nearby.
- **Other players' big wins are heard nearby:** a rare hatch plays a chime at that player (with the light pillar), so the world sounds like people are winning ([[Game Design Rules]] › casino floor → theme park). Commons stay private.
- **Footsteps and jumps:** keep Roblox's defaults unless the game has a reason to change them.

## 7. Settings
- **Three controls in the settings menu:** Music, Sound, Mute. Boo Town defaults: music 0.55, sound 0.8. Saved with the player's data.
- They live in a menu tile, never on the HUD (5-item cap, [[UI Rules]]).

## 8. Where sounds come from
- **Our own sounds**, or **Roblox's own audio library** in the Creator Store (sounds and music Roblox licenses for use in experiences). Keep the asset ID and source of every sound in `Config.sounds`.
- **Never use other people's uploaded audio** without the rights. A "free" label is not permission ([[UI Rules]] › Assets and licenses), and private audio won't play in our game anyway.
- **Uploads:** upload under the same owner as the game (the user, or the group if the game moves). Roblox caps audio uploads per month, so batch them.
- **Every sound is trimmed** (no silence at the start, so it lands on time) and **leveled** so all sounds feel about equally loud before `Config` volumes are set.

## 9. In Roblox
- `Sound` objects kept in `ReplicatedStorage/Sounds`, grouped into `SoundGroup`s under `SoundService`: **Music**, **SFX**, **Ambient**. The settings sliders set the group volumes.
- **UI and personal sounds play on the client** (`SoundService:PlayLocalSound` or a local `Sound`), so other players don't hear your clicks.
- **Sounds everyone should hear** (a rare hatch nearby) are triggered by the server telling clients, each client plays it at that position.
- Load sounds before they are needed (`ContentProvider:PreloadAsync` for the first-minute sounds), so the first coin isn't silent.
- Clean up: stop and destroy one-shot `Sound`s when they end (`Ended`), and stop music when the player leaves.

## 10. From prototype to Roblox
| Prototype | Roblox |
|---|---|
| Web Audio synth (`sfx('coin', n)`) | An uploaded `Sound` per name, IDs in `Config.sounds` |
| Gain buses (master / sfx / music) | `SoundGroup`s: Music, SFX, Ambient |
| Streak pitch (`n * 60` Hz) | `PlaybackSpeed` stepped per streak |
| `Music.setSong(area)` | `Audio.setZone(zoneId)` with a crossfade |
| Audio starts after the first tap (browser rule) | Not needed in Roblox |

**In prototypes, name every sound by its event** (`coin`, `buy`, `no`, `hatch`, `reveal_rare`), so the port is a list of names to fill with asset IDs.

## Checklist before calling sound done
- [ ] Every button and reward has a sound, and every sound has a visual partner
- [ ] Nothing loud, harsh or startling; music sits under the effects
- [ ] Same meaning = same sound family everywhere
- [ ] Streaks climb, repeats vary a little, spam is capped
- [ ] Rarity scales the reveal sound; no build-up that lies
- [ ] Music never stops, crossfades between zones, ducks during shows
- [ ] Music / Sound / Mute settings work and are saved
- [ ] Every sound ID is ours or Roblox-licensed, listed in `Config.sounds` with its source
- [ ] Sounds play in a live server (not just in Studio) and the first-minute sounds are preloaded

## Status
- **2026-10-29:** first draft at the user's request. Built from Boo Town's audio (separate music and sound volumes plus mute, a song per area, saved settings, nothing loud), Bounce for Eggs' streak pitch, the project rules and [[Game Design Rules]] › living soundscape. Not yet used on a ported game.
