[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/AgentGPTHuntrTest/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/AgentGPTHuntrTest/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-4k

A chess engine in 4,096 bytes of Python, entered in make.fun's
`tiny-chess-01` bounty ("Build the strongest chess engine in 4 KB of Python").

`main.py` is the whole engine: an lzma payload with its unpacker, 4,092 bytes
as committed. It speaks the bounty's env over HTTP (`POST /game`, `/move`,
`/resign` at `MAKEFUN_ENV_URL`), plays all eight gauntlet games, and exits.

Under the payload: a 0x88 board with incremental material/piece-square
evaluation and Zobrist hashing, pseudo-legal move generation with legality by
make-and-test, quiescence search over captures, promotions and check
evasions, and an iterative-deepening alpha-beta with a transposition table,
principal variation search, late move reductions, killer and history
ordering, and a fixed node budget per move (never a clock, so a replay plays
the same moves).

## Size rule

- `main.py`: 4,096 bytes at most, as committed. Compressed payloads count.
- Whole tree: 8,192 bytes, no file over 4,096. MIT license.

## Build

The unpacked source is not in the repository (the tree cap forbids it); the
payload is the source.

## License

MIT, see `LICENSE`.
