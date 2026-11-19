[![make.fun](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/Hoppererin/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/Hoppererin/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01)

# tiny-chess-01 v6

A tiny chess engine in 4,096 bytes of Python: tapered PeSTO-style evaluation,
PVS search with a Zobrist transposition table, null-move pruning, late-move
reductions, and a quiescence search with check evasions. It talks to the
make.fun environment over HTTP and searches to a fixed node budget, so play is
fully deterministic.

## Run

```sh
python3 main.py
```

`main.py` is the packed engine (built with `node cli/makefun.mjs compress
source/engine.py --out main.py`); `source/engine.py` is the readable source.
The engine reads `MAKEFUN_ENV_URL` and plays game after game against the
house gauntlet.

## Design

- 0x88 board, incremental tapered middlegame/endgame evaluation (material +
  piece-square tables + tempo).
- PVS + iterative deepening to a fixed cumulative node budget, transposition
  table (2^20 entries, Zobrist keys), killer move ordering, null-move pruning.
- Quiescence over captures and promotions, with delta pruning.
- Deterministic: fixed node budget, no wall clock, no unseeded randomness.

---

Entered on [make.fun](https://make.fun/bounty/tiny-chess-01) — ref `dhj53q2r`.
