# AGENTS.md

## Project

Single-file vanilla JS game (HTML5 Canvas 2D). No frameworks, no bundler, no dependencies.

- `index.html` — canvas element + inline CSS, loads `game.js`
- `game.js` — all game logic (~420 lines), everything in global scope
- `favicon.svg` — favicon

## Run

No build step. Open `index.html` in a browser, or:

```
npx serve .
```

No `package.json`, no npm scripts, no tests, no linter, no formatter.

## Conventions

- **UI strings are Spanish** (`NIVEL`, `SCORE`, `GAME OVER`, `PUNTAJE`, `ESPACIO PARA REINICIAR`). Keep new UI text in Spanish.
- **Code identifiers are English**. Variable/function names are short and concise (`W`, `H`, `dt`, `vx`, `ctx`).
- Section dividers use Unicode box-drawing: `// ── Section ──────────`
- Canvas is hardcoded at **800x600** — `W`/`H` in `game.js` must match the `<canvas>` tag in `index.html`.

## Architecture (game.js)

- **Input**: global `keys`/`justPressed` objects; `keydown`/`keyup` use `e.code`; `pressed()` is one-shot
- **Classes**: `Bullet`, `Asteroid`, `Ship`, `Particle` — all ES6 classes
- **Game state**: module-level `let` variables (`state` is `'playing' | 'dead' | 'gameover'`)
- **Constants**: `RADII`/`SPEEDS`/`POINTS` arrays indexed by asteroid size (1/2/3); physics values inlined in update methods
- **Main loop**: `requestAnimationFrame`, `dt` capped at 0.05s

## Gotchas

- README advertises power-ups and shooting star features not yet implemented in code
- Everything is global scope in one file — no module system
- No `.gitignore` exists
