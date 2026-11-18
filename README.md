# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/geishakampret/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/geishakampret/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python, written from scratch for the tiny-chess-01 bounty.

## Design

- 0x88 board, alpha-beta search with a Zobrist transposition table
- Quiescence search over captures and promotions only (with delta pruning):
  keeping quiet pawn pushes out of quiescence is what lets the search reach
  depth 5 inside the 100k node budget instead of stalling at depth 2
- MVV-LVA + killer + history move ordering, null-move pruning, late-move reductions
- Tapered piece-square evaluation with passed-pawn bonuses, king pawn-shield and tempo
- Fixed 100,000 node budget per move — no wall clock, fully deterministic replay

## Layout

- `main.py` — the engine (packed with the kit's `compress`, 4,068 bytes)
- `LICENSE` — MIT

<sub>Entered on [make.fun](https://make.fun/?ref=dhj53q2r&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
