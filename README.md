# Endless Runner

Chrome Dino-style endless runner built with **Phaser 3** (CDN) + vanilla JS.
No build step required — single `index.html` file.

## Quick Start

```bash
# Python (built-in, recommended)
cd endless-runner
python3 -m http.server 8080
# → open http://localhost:8080

# OR: Node / npx
npx serve . -p 8080
```

## Custom Player Sprite

Drop any PNG into `assets/player.png` before starting the server.
If the file is missing the game generates a green placeholder face automatically.

- Recommended size: **64 × 64 px** (square)
- Works with any resolution — displayed at 64 × 64 in-game

## Controls

| Action | Desktop        | Mobile        |
|--------|----------------|---------------|
| Jump   | Space / ↑ / W  | Tap anywhere  |
| Duck   | ↓ / S (hold)   | Swipe down    |

## Obstacle Types

| Type    | How to avoid           |
|---------|------------------------|
| Short   | Jump                   |
| Tall    | Jump                   |
| Flying  | Duck under or jump over|

## Game Rules

- Scroll speed starts at **280 px/s** and increases by **+30 px/s** every **500 points**
- Speed caps at **900 px/s**
- High score is persisted in `localStorage` — survives page refreshes
- **Coyote time**: 80 ms grace window after walking off the edge

## File Structure

```
endless-runner/
├── index.html      # Everything — Phaser CDN + all game logic (heavily commented)
├── assets/
│   └── player.png  # Drop your face PNG here
└── README.md
```

## Tweakable Constants

All magic numbers are centralised in the `C` object near the top of `index.html`:

```js
const C = {
  BASE_SPEED:  280,   // starting scroll speed (px/s)
  SPEED_INC:    30,   // speed added per milestone
  MILESTONE:   500,   // score points between speed bumps
  JUMP_VY:    -760,   // jump strength (more negative = higher)
  GRAVITY:    2200,   // falling acceleration (px/s²)
  COYOTE_MS:    80,   // coyote time window (ms)
  // ... etc.
};
```
