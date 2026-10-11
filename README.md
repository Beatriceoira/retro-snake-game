# retro-snake-game
Based on the classic 1997 snake game, in one HTML file.

# Retro Snake

A classic Snake game in a single `retro-snake.html` file. Vanilla JavaScript and the HTML5 `<canvas>` API, with no dependencies and no build step.

## Run it

Open `retro-snake.html` in any modern browser. That's it.

## Controls

| Input             | Action                                    |
| ------------------| ------------------------------------------|
| Arrow keys / WASD | Steer the snake                           |
| Space             | Pause, resume, or restart after game over |
| Swipe (touch)     |Steer the snake                            |
| Tap (touch)       | Pause, resume, or restart                 |

## Rules

- Eat the food square to grow by one segment and score 10 points.
- The game ends if the snake hits a wall or its own body.
- Your best score is saved in the browser (`localStorage`).

## How it works

| Concept             | Where to look                                                                                   |
| --------------------| ----------------------------------------------------------------------------------------------- |
| Game loop           | `setInterval(tick, 100)` runs one step every 100 ms                                             |
| Grid                | 400×400 canvas split into 20×20 px cells (20 columns × 20 rows)                                 |
| Velocity vector     | `dx, dy` hold the current direction; arrow keys change them via `steer()`.                      |
| Body shifting       | `snake.unshift(head)` adds the new head; `snake.pop()` removes the tail unless food was eaten.  |
| Input queue         | Up to 3 buffered turns, so fast key presses aren't lost and the snake can't reverse into itself |
| Collision detection | In `tick()`: bounds check for walls, `snake.some(...)` for self-hits                            |
| Rendering           | `draw()` clears the canvas and fills colored rectangles for food and each segment               |

## Project structure

```
retro-snake.html   # markup, styles, and game logic
README.md
```

## Learning goals

- Game loops (`setInterval` or `requestAnimationFrame`)
- Array manipulation for the snake's body
- Keyboard event listeners
- Collision detection
