# Asteroids — Agent Instructions

## Project Overview
Vanilla JS Asteroids clone using HTML5 Canvas. Single-file game logic in `game.js`. No dependencies, no bundler, no build step.

## Run
```bash
npx serve .
# then open http://localhost:3000
```
Or open `index.html` directly in browser.

## Structure
- `index.html` — entry point, loads `game.js`
- `game.js` — all game logic (Ship, Asteroid, Bullet, Particle, game loop)
- `favicon.svg` — app icon

## Key Conventions
- ES6 classes for entities (Ship, Asteroid, Bullet, Particle)
- Toroidal wrapping via `wrap(v, max)` utility
- Fixed timestep loop with `requestAnimationFrame`, clamped `dt <= 0.05`
- Input via global `keys` / `justPressed` objects
- No external deps — browser APIs only

## Testing / Linting
None configured. No test files, no lint config, no typecheck.

## Modifying Game Logic
Edit `game.js` directly. Constants at top of classes control behavior:
- `RADII`, `SPEEDS`, `POINTS` arrays (asteroid size tiers)
- `ROT`, `THRUST`, `DRAG` in `Ship.update`
- `SPEED`, `ttl` in `Bullet`
- Canvas size: `W=800`, `H=600` (also in `index.html`)

## Gotchas
- No module system — all code shares global scope
- `wrap()` handles negative coords correctly: `((v % max) + max) % max`
- Invincibility blink uses `Math.floor(invincible * 8) % 2`
- Game state: `'playing'` | `'dead'` | `'gameover'`