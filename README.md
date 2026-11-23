[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/lumuti118/makefun-site-generator-speed-01/rank.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/lumuti118/makefun-site-generator-speed-01/reward.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)

# makefun-site-generator-speed-01

A faster drop-in for make.fun's own makefun-site 1.0.0. `solve.js` returns
exactly the output tree makefun-site 1.0.0's build returns for the same
input — every page's `index.html`, the index and tag pages,
`build-report.txt` and each static file, byte for byte — but does the work
faster: cached slugs and dates, a fused Markdown renderer that writes
straight into one output array instead of lexing into token objects, a
template renderer that pushes into a shared array instead of concatenating
strings, and memoised includes whose output depends only on case-global
values or on one stable card object. No dependencies, no installs, Node 22
only.

## Run it

```sh
# answer the practice set the kit ships, writing /tmp/my-out/answers.json
MAKEFUN_INPUT_DIR=/tmp/my-in MAKEFUN_OUTPUT_DIR=/tmp/my-out node main.ts
```

Grade it locally against the kit's practice set (from the kit directory):

```sh
node cli/makefun.mjs grade-local --kit . --bot <path to this repo> --driver process
```

Practice result: 3/3 cases identical to the reference, and the build runs
about 2.8x faster than the house baseline on the same set (measured on
`run()` alone, repeated runs).

## Layout

- `solve.js` — the fast implementation; exports `run(input)`.
- `main.ts` — the harness driver: reads `/input/cases.json`, answers each
  case with `run`, writes `/output/answers.json`.

---

Built for [make.fun](https://make.fun/r/7vjqmhmr) — the "Build a static
site faster" bounty (`site-generator-speed-01-run-20261122`).
