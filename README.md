# slide-engine

A single-file HTML slide deck with a real presenter mode. No build step, no dependencies, works offline. Copy `template.html`, rename it, write slides.

## Presenting

Open the file in Chrome, press **S** for the speaker window, and share only the deck window.

| Key | Does |
| --- | --- |
| → / space | Next click or slide |
| ← | Back |
| S | Speaker window: current and next slide previews, notes, timer, pacing |
| T / R | Start-pause / reset the timer |
| O / Esc | Grid of every slide, click to jump |
| G | Go to slide number |
| N | Notes drawer in the same window (single-screen fallback) |
| H | Handout view: every slide with its notes, for prep |
| F | Fullscreen |
| ? | Key list |

The speaker window runs its own clock, so it keeps counting when the browser throttles a background window.

## Writing slides

Each slide is a `<section class="slide">`. The template has one of each kind: title, a click-building content slide with a diagram, a break slide with a countdown, and an end slide.

- `data-min="3"` is the expected length. The speaker window shows a target and how far ahead or behind you are.
- `class="frag" data-step="1"` reveals on click 1. Everything sharing a step appears together, and numeric steps play in number order regardless of where they sit in the file.
- `data-say="..."` labels a click in the speaker view.
- `<aside class="notes-src">` holds the notes. `<p class="cue">[ CLICK 1 ]</p>` renders as a click marker.
- Layout helpers: `cols`, `cols.wide-left`, `cols.wide-right`, `cols3`, `stack`, `fill`, `rule-box`, `rule-box.tight`, `card`, `chat`.
- SVG classes: `node`, `node-a`, `node-t`, `edge`, `edge-a`, `lbl`, `lbl-s`, `lbl-a`, `lbl-t`, `cell`, `cell-a`, `cell-t`, `wall`, `badge`, `dist`.

Two things that go wrong:

- Give SVGs explicit `width` and `height`. Without them they scale to the column width and push the slide past the bottom.
- Draw highlight edges before the circles, or stop them at the circle's edge. Otherwise the line paints over the node letters.

## PDF

Ctrl+P, Save as PDF, Landscape, and turn on **Background graphics**. One slide per page, every click revealed, notes hidden, dark theme kept.

## License

MIT
