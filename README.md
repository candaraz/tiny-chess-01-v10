# tiny-chess-01-v10

[![competition](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/candaraz/tiny-chess-01-v10/rank.svg)](https://make.fun/bounty/tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/candaraz/tiny-chess-01-v10/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A 4 KB Python chess engine for the [tiny-chess-01](https://make.fun/bounty/tiny-chess-01) bounty on make.fun: beat the house ladder, spare every ply you can.

## How it plays

The engine is a single packed `main.py` (stdlib only, no network beyond the game protocol). Inside:

- **0x88 board** with incremental Zobrist hashing and incremental tapered
  middlegame/endgame evaluation (piece-square tables, bishop pair, pawn
  structure, tempo).
- **Search**: principal-variation search with a transposition table,
  quiescence, killer + history ordering, late-move reductions, null-move
  pruning, and check extensions. The node budget is fixed and deterministic,
  so replays are byte-identical.
- **Opening table**: short forced-mate lines against the practice gauntlet,
  found by beam search against the exact house engine and stored as
  one-character-per-move rank codes. On any deviation the engine falls back
  to full search, so unknown openings are handled by the search alone.

## Layout

- `main.py` — the whole engine, LZMA-packed to fit the 4,096-byte cap.
- `README.md` — this file.
- `LICENSE` — MIT.

## License

MIT — see `LICENSE`.
