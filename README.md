# 🌊 Boat Adventure

A single-file, browser-based 3D naval adventure built with **Three.js**. Sail a steam-powered boat across a stylized, cel-shaded ocean inspired by *The Legend of Zelda: The Wind Waker* and *Zelda: Phantom Hourglass*. Battle phantom ships, dodge icebergs and whirlpools, haul sunken treasure from the deep, and upgrade your vessel into an ironclad juggernaut — all while the sun sets, storms roll in, and leviathans rise from the deep.

Just open `index.html` in a modern browser and set sail. No build step, no dependencies beyond an internet connection for the Three.js CDN.

![Game View](screenshots/view.png)

![Game Map](screenshots/map.png)

---

## ✨ Features

- **Cel-shaded toon ocean** with animated Gerstner-style waves, foam, and stylized specular highlights
- **Full day/night cycle** with orbiting sun & moon, stars, sunset tinting, and 1x / 4x / 16x timelapse speeds
- **Dynamic weather ladder**: Calm Waters → Stormalong Fog → Squall & Rain → GREAT STORM → Frozen Polar Sea, with lightning flashes, wind drift, and rain
- **Center-reticle aiming** — orbit the camera and fire cannons exactly where the crosshair points (third-person over-the-shoulder)
- **Two cannon styles**: 💥 *Double Potence* (1 mega shell) or ⚡ *Double Balls* (2 twin shells, half damage each)
- **7 enemy types** with floating health bars: Pirate Raider, Phantom Galleon, Phantom Sky Drake, Abyssal Gulper, Dread Kraken, Giant Sea Serpent, Titan Dreadnought
- **Environmental hazards**: rocks, lily-pad plants, icebergs & ice floes, tropical islands, and whirlpools (which drag you in and damage your hull)
- **Deep-sea treasure beacons** — columns of light mark sunken chests; drop the salvage crane to haul up loot with random rarity tiers
- **Sea Chart autopilot** — draw a route on the parchment map and the boat follows it
- **Live mini-map** with hazards, enemies, treasure, and route overlay
- **Ship growth** — hull, boiler, turbine, and cannons visually scale as you upgrade
- **Procedural audio** synthesized via Web Audio API (cannons, splashes, treasure chimes, boost, crane)
- **Auto-save** to `localStorage` every 5 seconds (plus manual Reset)

---

## 📜 Legend

| Icon | Meaning |
|---|---|
| ⛵ | Player Boat / Pirate Raider |
| 💀 | Phantom Ship |
| 🐉 | Leviathan |
| 🐙 | Kraken |
| 🐟 | Angler |
| 🦅 | Flying Drake |
| 🏴‍☠️ | Titan Dreadnought |
| 🌿 | Plants |
| ❄️ | Ice |
| 💎 | Deep Light (treasure) |

---

## 🎮 Controls

| Input | Action |
|---|---|
| **Mouse move** | Orbit camera / aim center reticle (pointer-lock or click-drag) |
| **Left Click** or **F** | Fire cannons |
| **W / S** or **↑ / ↓** | Throttle forward / reverse |
| **A / D** or **← / →** | Steer |
| **SPACE** | Jump over obstacles / clear charted route |
| **SHIFT** | Activate Propulsor Boost |
| **E** | Drop salvage crane (when near a treasure beacon) |
| **M** | Open / close full Sea Chart |
| **Mouse Wheel** | Zoom camera in/out |

---

## ⚓ Ship Upgrades

Earn **XP** from sinking enemies, collecting XP orbs, and salvaging treasure. Spend it in the top-right panel. Every upgrade **doubles** its stat, and the ship model visibly grows.

| Upgrade | Base Stat | Cost (Lv 0) | Effect |
|---|---|---|---|
| 🛡️ **Boat Defense** | 50 HP | 40 XP | Doubles Max HP (50 → 100 → 200 → …) |
| ⚙️ **Engine Speed** | 50 | 45 XP | Doubles top sailing speed |
| 💣 **Cannon Attack** | 50 | 50 XP | Doubles attack damage |
| 🚀 **Propulsor Boost** | 1.0 s | 50 XP | Doubles boost duration (1s → 2s → 4s → …) |

Costs scale by `base × 2.1^tier`, so plan your spending.

---

## 🗺️ The Sea Chart

Press **M** or click the map button to open the full **parchment Sea Chart**:

- **Click & drag** on the chart with your "quill" to draw a route for the boat to follow automatically.
- A glowing autopilot badge appears while a route is active — press **SPACE** to clear it.
- The chart shows boats, enemies (each with its own icon), hazards, treasure beacons, and a compass rose.

---

## 🌦️ World Systems

- **Time** advances continuously; watch the badge in the top-left to see the current hour and phase (Dawn / Daylight / Dusk / Night).
- **Weather** cycles on its own timer, or you can force progression by watching the banner. Great Storms summon lightning and heavy seas; the Frozen Polar Sea spawns ice hazards.
- **Wind** drifts clouds and pushes your boat, growing stronger in storms.

---

## 💾 Saving & Reset

- Progress (XP bank, kills, treasures, upgrade tiers, cannon style, current HP) auto-saves to your browser's `localStorage`.
- Use the **↺ Reset** button in the stats panel to wipe your save and start fresh.

---

## 🛠️ Tech Notes

- **Single HTML file** — all CSS, JavaScript, and game logic inline.
- **Three.js r160** loaded via import map from unpkg CDN.
- Shaders written as inline GLSL for the sky dome and ocean surface.
- Game objects (projectiles, particles, wake rings, smoke puffs, flashes) use **object pooling** to avoid garbage collection hitches.
- Includes a `selfTest()` routine that validates default stats, doubling math, cannon modes, and the aiming/camera pipeline — visible in the browser console on load.
- A `window.game` object exposes `player`, `hazards`, `treasures`, `enemies`, and key functions for debugging in the console.

---

## 🚀 Getting Started

```bash
# Clone or download, then simply open the file:
open index.html      # macOS
start index.html     # Windows
xdg-open index.html  # Linux
```

Or serve locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

> **Requires** a modern browser with WebGL and pointer-lock support (Chrome, Edge, Firefox, Safari).

---

*Set your course, hoist the sail, and may the storms spare your hull.* ⚓🌩️