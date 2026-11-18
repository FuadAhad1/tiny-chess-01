[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/FuadAhad1/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/FuadAhad1/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# Tiny chess engine (v11)

A 4,022-byte Python chess engine for the [make.fun tiny-chess-01 bounty](https://make.fun/bounty/tiny-chess-01).
0x88 board, negamax alpha-beta with iterative deepening (depths 1-5), a
fixed 120,000-node budget per depth (no wall clock), quiescence over
captures/promotions and replies to check, MVV-LVA capture ordering, killer
moves, material + mirrored piece-square evaluation, bishop-pair bonus, and
delta pruning in quiescence (a capture is skipped when static eval + victim
value + 150 still cannot reach alpha; not in check or on promotions). The
engine is shipped as an LZMA payload that unpacks and runs at import; the
packed file is all of main.py.

Verified full 16-game trials against the house gauntlet (mean Elo): v10
1,200 (1,253 / 1,173 / 1,173); v11 1,226 (1,290 / 1,173 / 1,214). The
sunfish baseline mean is 1,360. Deterministic: no wall clock, no unseeded
randomness, no model calls, stdlib only.

Build: the raw source is work/v10delta.py (10,250 bytes); work/pack.py
packs it into main.py. Every Elo above comes from a completed trial's
scores.json, run with the kit's local grader.
