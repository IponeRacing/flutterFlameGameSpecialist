# Flutter Flame Game Specialist

> A Claude Code sub-agent that builds production-quality Flutter 2D games with the
> **Flame engine** — sprites, tilemaps, physics, audio, camera, parallax, and Flutter HUD
> overlays. Knows every major **CC0/royalty-free asset source** by game type and license.

[![License: MIT](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)
[![Flutter](https://img.shields.io/badge/Flutter-3.27%2B-02569B?logo=flutter)](https://flutter.dev)
[![Flame](https://img.shields.io/badge/Flame-1.20%2B-FF6B35)](https://flame-engine.org)

---

## What it delivers

| Feature | Technique |
|---------|-----------|
| 🎮 Sprite rendering | `SpriteComponent` + `FilterQuality.none` for crisp pixel art |
| 🏃 Multi-state animation | `SpriteAnimationGroupComponent<State>` (idle/run/jump/attack) |
| 🗺️ Tilemap loading | `TiledComponent` + Tiled Editor workflow with Kenney tilesets |
| 🌅 Parallax backgrounds | `ParallaxComponent` with velocity multiplier per layer |
| 🔊 Audio | `flame_audio` pre-loaded in `onLoad()`, BGM + SFX |
| 🎯 Collision | `RectangleHitbox` + `CollisionCallbacks` + `HasCollisionDetection` |
| 📷 Camera | `CameraComponent.withFixedResolution()` + `follow()` + bounds |
| ⚙️ Physics | `flame_forge2d` Box2D with `BodyComponent` pattern |
| 🖥️ HUD / Menus | Flutter `GameWidget` overlays with `ValueNotifier` bridge |
| 🎨 Pixel fonts | Google Fonts `Press Start 2P`, `VT323`, `Silkscreen` |
| 📦 TexturePacker | `flame_texturepacker` for multi-atlas sprite sheets |
| 🧱 RPG extension | `bonfire` top-down RPG layer on Flame |

---

## Free CC0 Asset Sources (built into agent knowledge)

### 🥇 Kenney.nl — The Gold Standard

**License: CC0 (public domain) — zero attribution required**

| Pack | Game type | Tile size |
|------|-----------|-----------|
| Platformer Pack | Platformer | 64×64 |
| Pixel Platformer | Pixel platformer | 16×16 |
| RPG Urban Pack | Top-down RPG | 16×16 |
| Tiny Town | Top-down RPG | 16×16 |
| Space Shooter Redux | Space shooter | varies |
| UI Pack | All games HUD | varies |
| Game Icons | All games | 64×64 |
| Interface Sounds | UI SFX | .ogg/.mp3 |
| RPG Audio | RPG SFX | .ogg/.mp3 |

> 60,000+ assets, all CC0, vectors included. Download from [kenney.nl/assets](https://kenney.nl/assets).

### 🟢 Other CC0 Sources

| Source | Best for | URL |
|--------|----------|-----|
| 0x72 (Itch.io) | Dungeon tileset + animated chars | 0x72.itch.io/dungeontileset-ii |
| OpenGameArt CC0 | Varied sprites, music, SFX | opengameart.org/content/cc0-resources |
| Superpowers Packs | Themed complete kits | github.com/sparklinlabs/superpowers-asset-packs |
| SONNISS GDC Bundle | Pro SFX library (20GB+/year) | sonniss.com/gameaudiogdc |
| Freesound.org | SFX (filter CC0) | freesound.org |
| Google Fonts | Pixel fonts (OFL) | fonts.google.com |
| Public Pixel Font | Multilingual pixel font | ggbot.itch.io/public-pixel-font |

### 🔵 Royalty-Free (attribution not required, cannot redistribute)

| Source | Quality | URL |
|--------|---------|-----|
| CraftPix Freebies | ⭐⭐⭐⭐⭐ | craftpix.net/freebies |
| GameArt2D | ⭐⭐⭐⭐ | gameart2d.com/freebies.html |
| Mixkit SFX | ⭐⭐⭐⭐ | mixkit.co/free-sound-effects/game |

---

## Installation

### Project-level

```bash
mkdir -p your-project/.claude/agents
cp agents/flutter-flame-game-specialist.md your-project/.claude/agents/
```

### Global (all Claude Code sessions)

```bash
mkdir -p ~/.claude/agents
cp agents/flutter-flame-game-specialist.md ~/.claude/agents/
```

---

## Usage examples

```
Set up a Flame platformer project:
- Virtual resolution 640×360
- Kenney Pixel Platformer tileset loaded via Tiled
- Player with idle/run/jump animations (SpriteAnimationGroupComponent)
- Parallax background with 4 layers
- Coin pickup with SFX from Kenney Interface Sounds
- Score HUD as Flutter overlay with Press Start 2P font
```

```
Add flame_audio to the existing Flame game:
- Pre-load all SFX in onLoad()
- Background music loop with pause/resume on app lifecycle
- Coin collect, jump, hit, level complete sounds from Kenney CC0 packs
```

```
Build a top-down RPG level from a Tiled .tmx map:
- TiledComponent loading level_01.tmx
- Object layer to spawn Player, Enemies, Items
- Collision layer mapped to RectangleHitbox
- CameraComponent following the player within level bounds
```

---

## Packages used

```yaml
flame: ^1.20.0
flame_audio: ^2.10.0
flame_tiled: ^1.20.0
flame_texturepacker: ^1.9.0
flame_forge2d: ^0.19.0
bonfire: ^3.12.0          # optional: RPG extension
google_fonts: ^6.2.1
```

---

## Anti-patterns prevented

| ❌ Common mistake | ✅ Correct |
|------------------|-----------|
| `images.load()` in `update()` | Load once in `onLoad()`, store in field |
| HUD drawn in Flame `render()` | Use `GameWidget` overlay (Flutter widgets) |
| Legacy `Camera` class | `CameraComponent.withFixedResolution()` |
| `FilterQuality.high` on pixel art | `FilterQuality.none` for crisp pixels |
| No `HasCollisionDetection` mixin | Add to `FlameGame` — hitboxes won't fire without it |
| CC-BY asset without credits screen | Use CC0 only, or add proper attribution |
| Large `.wav` audio files | `.mp3` for music, `.ogg` for SFX |

---

## Related agents

- **flutter-ui-specialist** — Candy gradients, liquid glass, spring animations for Flutter app UI (menus, onboarding, non-game screens)
- **flutter-payment-specialist** — Apple StoreKit 2, Google Play Billing, Stripe for monetizing your game

---

## License

MIT — [EngageEngine](https://engageengine.ch)
