# Cellarium Life

An infinite-grid cellular automaton lab for the browser: paste RLE patterns, pick a B/S rule, and pan and zoom across an unbounded plane.

**Status: early scaffold.** The repository currently contains the Vite + TypeScript project shell; the automaton lab described above is not implemented yet. `PLAN.md` describes the intended implementation.

## Planned

- Sparse unbounded grid (Map-based live cells)
- RLE import/export and a built-in pattern library (glider, LWSS, Gosper gun, pulsar, R-pentomino, acorn)
- Custom B/S rule strings (e.g. `B3/S23`, `B36/S23`) with live editing
- Pan/zoom canvas, draw/erase, speed control, step, clear, randomize

## Run

```bash
npm install
npm run dev
npm test
npm run build
```

## License

MIT
