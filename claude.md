# Snake Web Game

A modern, visually polished Snake game built with HTML5 Canvas and vanilla JavaScript.

## Project Structure

```
/home/harness/cyops_data/workspace/tanchis/
└── index.html          # Complete game: HTML + CSS + JS
```

## Development Standards

### Code Style
- Use vanilla JavaScript (ES6+ classes)
- No external dependencies
- Single-file architecture
- Clean separation: Game class manages state, render, input

### Canvas Configuration
- Logical size: 600x600 pixels
- Grid: 20x20 cells (30px per cell)
- Game tick: 100ms (10 moves/second)
- Render loop: 60 FPS via requestAnimationFrame

### Game State Management
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

### Input Handling
- Keyboard: Arrow keys + WASD
- Prevent 180-degree turns
- Touch: swipe detection for mobile

### Visual Design System
- Background: radial-gradient(circle at center, #1a1a2e 0%, #0f0f1a 100%)
- Snake: linear-gradient(135deg, #00d4aa 0%, #00a884 100%)
- Food: #ff4757 with glow animation
- UI Font: 'Segoe UI', system-ui, sans-serif
- Score Font: monospace
