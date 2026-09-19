# Cellarium Life

Infinite-grid cellular automaton lab in the browser.

Paste any RLE pattern, pick a B/S rule, hit play, and pan/zoom across an unbounded plane while generation and population counters tick.

## Features

- Sparse unbounded grid (Map-based live cells)
- Pan + wheel zoom around cursor
- RLE import / export
- Built-in pattern library (glider, LWSS, Gosper gun, pulsar, R-pentomino, acorn) with live thumbnails
- Live rule string input (`B3/S23`, `B36/S23`, …)
- Draw / erase, speed control, step, clear, randomize
- Optional cell-age coloring

## Tech

Core (`src/core`) is pure TypeScript / DOM-free and unit-tested. UI is canvas + vanilla TS.

## Run

```bash
npm install
npm run dev
npm test
```

## License

MIT
