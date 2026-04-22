# Wumpus World — Interactive AI Textbook Companion

A fully interactive, browser-based implementation of the **Wumpus World** environment from **Russell & Norvig's *AI: A Modern Approach*** (Section 7.2). Built as a single offline-capable HTML file — no dependencies, no build step.

![Game Modes](https://img.shields.io/badge/modes-5-blue) ![Tests](https://img.shields.io/badge/tests-64%2C913%20passed-brightgreen) ![Offline](https://img.shields.io/badge/offline-PWA-orange)

## Why This Exists

The Wumpus World is the canonical teaching environment for **logical inference under uncertainty** in AI courses worldwide. This project makes it tangible — students can play the game, observe percepts, and practice the exact reasoning from Chapters 7, 13, and beyond.

## Features

### 5 Textbook-Accurate Game Modes

| Mode | Grid | Sensors | Movement | Wumpi | Reference |
|------|------|---------|----------|-------|-----------|
| **Classic** | 4×4 | Perfect | Deterministic | 1 | Ch. 7 — Logical Agents |
| **Stochastic** | 4×4 | Perfect | 20% slip | 1 | Ch. 13 — Probabilistic Reasoning |
| **Noisy Sensors** | 4×4 | Stench/Breeze flip 10% | Deterministic | 1 | Ch. 13 — Sensor Models |
| **Large Cave** | 6×6 | Perfect | Deterministic | 2 | Scaled environment |
| **Nightmare** | 6×6 | Noisy | 20% slip | 2 | All challenges combined |

### Game Mechanics (100% Textbook-Aligned)

- **Percepts**: Stench (adjacent to Wumpus), Breeze (adjacent to pit), Glitter (on gold cell)
- **Actions**: Move (4 directions), Turn Left/Right, Grab, Shoot, Climb
- **Directional arrow**: Flies straight in facing direction until hitting Wumpus or wall
- **Scoring**: +1000 escape with gold, −1000 death, −1 per action, −10 per arrow
- **Gold placement**: BFS-guaranteed reachable from start cell (pits block, Wumpus can be killed)

### Pedagogical Tools

- **Knowledge Base**: Real-time display of inferred safe/unsafe cells
- **Context-Sensitive Hints**: Togglable hints teaching logical reasoning from Section 7.2
- **Study Guide**: Collapsible textbook reference with formulas and chapter citations
- **Rules & Controls**: In-game reference panel

### Technical

- **Single HTML file** — zero dependencies, works offline
- **Mobile-friendly** — touch controls, responsive layout
- **PWA-capable** — installable on phones for study sessions
- **Exhaustively tested** — 64,913 automated assertions + 1,520 Playwright browser gameplay tests across all modes

## Play

Open `index.html` in any browser. That's it.

```bash
# Or serve locally
python3 -m http.server 8000
# → http://localhost:8000/index.html
```

## Testing

The simulation suite validates every textbook rule:

```bash
node simulate.js
```

Verifies:
- World generation constraints (start cell safety, gold reachability via BFS)
- Percept accuracy (stench, breeze, glitter, noisy sensor flipping)
- All agent actions (move, turn, shoot, grab, climb)
- Scoring arithmetic (perfect game = 995 points)
- Stochastic mechanics (~20% slip rate)
- Noisy sensors (stench/breeze flip, glitter never flips)
- Edge cases (wall bumps, dead wumpus traversal, post-game-over blocking)

## Controls

| Action | Keyboard | Mobile |
|--------|----------|--------|
| Move | Arrow keys / WASD | Direction buttons |
| Turn Left | Q | ↩ button |
| Turn Right | E | ↪ button |
| Grab gold | G | ✋ Grab |
| Shoot arrow | F | 🏹 Shoot |
| Climb out | C | 🧗 Climb |

## References

- Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th ed.). Pearson.
  - Section 7.2: The Wumpus World
  - Section 7.4: Propositional Logic
  - Section 13.1: Uncertainty and Probabilistic Reasoning

## License

MIT
