## Goal
Create a visually polished Snake web game with smooth animations, modern UI design, and complete game mechanics including score tracking, high score persistence, and mobile-friendly controls.

## Context
- **Working directory**: `/home/harness/cyops_data/workspace/tanchis` (empty git repository)
- **Target**: Single-page web application, no build tools required
- **Tech stack**: HTML5 Canvas + vanilla JavaScript + CSS3
- **Design approach**: Modern glassmorphism/dark theme with neon accents, responsive layout

## Acceptance Criteria

- **AC-1: Core Game Mechanics**
  - Snake moves continuously in four directions (arrow keys or WASD)
  - Snake grows by 1 segment when eating food
  - Game ends on wall collision or self-collision
  - Food spawns randomly on unoccupied grid cells
  - Score increments by 10 points per food eaten

- **AC-2: Visual Design**
  - Dark theme background (`#0f0f1a` or similar deep color)
  - Snake rendered with gradient fill (green/cyan neon style)
  - Food rendered as glowing orb with pulse animation
  - Grid overlay with subtle lines for visual reference
  - Score display with large, readable typography
  - Game overlay screens (start, game over, pause) with blur/glassmorphism effect

- **AC-3: UI/UX Features**
  - Start screen with "Press Space or Click to Start"
  - Game Over screen showing final score and high score
  - Pause functionality (P key)
  - High score persisted to `localStorage`
  - Smooth canvas rendering at 60 FPS using `requestAnimationFrame`
  - Visual feedback on food consumption (particle burst effect)

- **AC-4: Mobile Responsiveness**
  - Canvas scales to fit viewport (max 600px width)
  - Touch/swipe controls for mobile devices
  - On-screen directional buttons for mobile (optional but recommended)
  - Prevent page scroll on touch to keep game in view

- **AC-5: Code Structure**
  - Single HTML file (`index.html`) embedding CSS and JS
  - No external dependencies (pure vanilla JS)
  - Game state managed via `Game` class
  - Separated concerns: rendering, input handling, game logic

## Implementation Notes

**File Structure:**
```
/home/harness/cyops_data/workspace/tanchis/
└── index.html          # Complete game: HTML + CSS + JS
```

**Key Technical Decisions:**
- Canvas size: 600x600 logical pixels, CSS-scaled for responsiveness
- Grid system: 20x20 cells (30px per cell)
- Game speed: 100ms per tick (10 moves/second), adjustable via difficulty
- Animation loop decoupled from game tick for smooth effects

**CSS Design System:**
- Background: `radial-gradient(circle at center, #1a1a2e 0%, #0f0f1a 100%)`
- Snake: `linear-gradient(135deg, #00d4aa 0%, #00a884 100%)` with `#00ffc8` highlight
- Food: `#ff4757` with `box-shadow` glow animation
- Font: `'Segoe UI', system-ui, sans-serif` for UI; `monospace` for scores

**JavaScript Architecture:**
```javascript
class SnakeGame {
  constructor() { /* init canvas, state, event listeners */ }
  start() { /* reset state, start loop */ }
  update() { /* game tick: move snake, check collisions */ }
  draw() { /* render frame */ }
  handleInput(direction) { /* queue next direction */ }
  spawnFood() { /* random position not on snake */ }
  gameOver() { /* save high score, show overlay */ }
}
```

**Input Handling:**
- Keyboard: `ArrowUp/Down/Left/Right` and `W/A/S/D`
- Prevent 180-degree turns (instant death)
- Touch: track `touchstart`/`touchend` delta for swipe detection

**Risk Mitigation:**
- Use `will-change: transform` on canvas for GPU acceleration
- Debounce resize events to avoid layout thrashing
- Prevent default on arrow keys to stop page scrolling

## Out of Scope
- Multiplayer support
- Sound effects / audio
- Backend/high score leaderboard
- Progressive Web App features (service worker, offline)
- Different difficulty levels or game modes
- Customizable snake skins