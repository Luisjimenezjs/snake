# Snake

The classic Snake, in the browser.

## Play

Open `index.html` in a browser. No server, no build step.

## Controls

- Arrow keys or `WASD` to steer
- `Space` to pause and resume
- `R` to restart
- On touch: swipe to steer, tap to start, pause or restart

## How it works

Everything lives in `index.html` — markup, styles and game code in one file.

- A 20x20 grid drawn on a `<canvas>`, one cell per snake segment.
- A fixed-timestep loop: `requestAnimationFrame` accumulates elapsed time and
  runs a game step every `stepMs`, so speed does not depend on the refresh rate.
- Each food eaten shaves 3 ms off `stepMs`, down to a floor of 70 ms.
- Turns go through a short queue and are applied one per step, so a fast
  double-tap cannot reverse the snake into itself.
- The best score is kept in `localStorage`, wrapped in `try`/`catch` so a
  private window degrades to a working game with no saved best.
