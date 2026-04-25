# Wumpus World

Browser-based Wumpus World game from Russell & Norvig's *AI: A Modern Approach* (Section 7.2). Everything runs from a single HTML file, no build step or dependencies needed. Works offline, works on phones.

Built this to have something playable while studying the logical inference chapters. The five modes cover the main variants discussed in the textbook.

## Game Modes

| Mode | Grid | Sensors | Movement | Wumpi | Chapter |
|------|------|---------|----------|-------|---------|
| Classic | 4×4 | Perfect | Deterministic | 1 | Ch. 7 |
| Stochastic | 4×4 | Perfect | 20% slip | 1 | Ch. 13 |
| Noisy Sensors | 4×4 | Stench/Breeze flip 10% | Deterministic | 1 | Ch. 13 |
| Large Cave | 6×6 | Perfect | Deterministic | 2 | - |
| Nightmare | 6×6 | Noisy | 20% slip | 2 | All of the above |

## Mechanics

Follows the textbook rules closely:

- Stench when adjacent to Wumpus, breeze when adjacent to pit, glitter when on the gold cell
- Agent has a facing direction. Arrow shoots straight in that direction until it hits something or a wall
- Scoring: +1000 for escaping with gold, -1000 for death, -1 per action, -10 per arrow
- Gold is always placed on a cell reachable from the start (BFS check, pits block movement)

There's also a knowledge base overlay that shows inferred safe/unsafe cells, a hint system that nudges you toward the right logical deductions, and a collapsible study guide with chapter references.

## How to Play

Open `index.html` in a browser.

```bash
# or serve it
python3 -m http.server 8000
```

## Controls

| Action | Keyboard | Mobile |
|--------|----------|--------|
| Move | Arrow keys / WASD | Direction buttons |
| Turn Left/Right | Q / E | ↩ ↪ buttons |
| Grab gold | G | ✋ Grab |
| Shoot arrow | F | 🏹 Shoot |
| Climb out | C | 🧗 Climb |

## Tests

`simulate.js` runs ~65k assertions covering world generation, percepts, movement, turning, shooting, grabbing, climbing, scoring, stochastic slip rates, noisy sensor flipping, coordinate mapping, and edge cases. Also ran 1500+ automated playthroughs in Playwright across all modes.

```bash
node simulate.js
```

## References

Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th ed.), Sections 7.2, 7.4, 13.1.

## License

MIT
