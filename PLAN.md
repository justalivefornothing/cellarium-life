# Cellarium — plan

**Goal.** An infinite-grid cellular automaton lab in the browser: paste any RLE
pattern from the web, pick a B/S rule, hit play, and pan/zoom across an
unbounded plane while generation and population counters tick along.

## Features

- Sparse, unbounded grid — live cells live in a `Map` keyed by packed
  `(x, y)` coordinates; the plane has no edges.
- Pan (drag with space / middle mouse / right mouse) and wheel zoom around
  the cursor.
- RLE decoder for pasted patterns; RLE encoder for exporting the current
  live set (70-character line wrapping, minimal runs).
- Pattern library drawer: glider, LWSS, Gosper glider gun, pulsar,
  R-pentomino, acorn — each card shows a tiny live thumbnail that animates.
- Rule string input (`B3/S23`, `B36/S23`, `B2/S`, …) parsed and applied live.
- Draw / erase with the mouse; generation and population counters.
- Speed slider, single step, clear, randomize.
- Optional cell-age coloring (newborn cells ink-dark, old cells fade to sepia).

## Architecture

```
src/
  core/
    coords.ts     pack / unpack integer coordinates into a single number key
    rule.ts       parseRule("B36/S23") -> { birth: Set, survive: Set }, formatRule
    life.ts       World: sparse Map<key, age>; step() via neighbor-count Map
    rle.ts        decodeRLE / encodeRLE (run counts, b / o / $ / !, wrapping)
    patterns.ts   built-in library as RLE strings + metadata
  ui/
    renderer.ts   canvas draw: paper background, dotted grid, cells, age tint
    viewport.ts   camera (offset + scale), screen <-> cell math
    thumbnails.ts tiny per-card canvases that run their own World
  main.ts         wires DOM controls, input handling, animation loop
  style.css       cream paper theme, serif display, drawer, footer
```

The core (`src/core`) is DOM-free and fully covered by vitest. The UI layer
only depends on the core's public API.

## Milestones

1. Plan, license, git init.
2. Scaffold `vite` vanilla-ts, add vitest.
3. Core: coords, rule parser, sparse Life step, RLE codec — tests green.
4. Canvas renderer + viewport (pan / zoom) + draw / erase.
5. Toolbar (play / step / speed / clear / random / rule input / age toggle),
   RLE import + export panel.
6. Pattern drawer with live thumbnails; footer counters.
7. Build, headless smoke, screenshot, README, publish.
