# AGENTS.md

## Architecture

Single static page, no build step:

- `index.html` — everything: markup, Tailwind (via CDN script) utility classes, and a `<script>` block holding all app logic. There is no bundler, framework, or module system; all functions are attached to the global scope and wired up via inline `onclick`/`oninput` attributes.
- `netlify.toml` — publishes `.` directly; no `[build.command]`, since there is nothing to compile.

## Data flow

`fetchToniesDB()` fetches `toniesV2.json` from the `toniebox-reverse-engineering/tonies-json` GitHub repo at runtime (client-side, no server proxy). The raw shape is `[{ article, data: [{ series, episode, image, category, sample, ... }] }]` — one entry per article, with `data` holding per-language variants. It is flattened to the `{ title, series, category, pic, audioSample }` shape the UI works with, using `data[0]` (mostly `de-de`) and mapping the catalog's many raw `category` strings (`audio-play`, `Hörspiele & Hörbücher`, `music`, …) onto the four labels the filter pills use (`Hörspiel`, `Musik`, `Wissen`, plus `Disney` which matches on `series` instead of `category`). If this mapping needs to change, update `CATEGORY_LABELS` in `index.html`.

All other state (`selectedTonie`, `transformState`, `printQueue`) lives in memory only — there is intentionally no persistence layer, since the print sheet is meant to be built and printed in one sitting.

## Print pipeline

The A4 sheet is not printed from `<img>` tags. `renderA4PrintGrid()` preloads every queued
motif via `Promise.all(printQueue.map(loadCapsuleImage))` and only then builds one
`.sheet-page` node per physical page, placing a `<canvas>` per motif at its absolute
millimetre slot (`slotPosition()`). `drawCapsule()` reproduces the editor preview exactly:
the motif is `contain`-fitted into the capsule box, centred, then offset/zoomed/rotated
like the CSS transform. `CAPSULE_PX` (43mm at 96dpi) is the shared coordinate system for
the editor preview, the sheet canvases, the curved text (`drawCapsuleText`) and the 300dpi
PNG export (`downloadSheetPNG`), so a canvas of any resolution can be derived from one
transform state. The same on-screen sheet is what the browser prints; there is deliberately
no second hidden print-only DOM copy (that duplicate used to print before its images had
loaded). Because the pages keep their true 210x297mm layout size, they are wider than a
phone screen — `fitSheetToViewport()` only shrinks them visually via `--sheet-scale` and
sizes the `.sheet-frame` wrapper to match; `@media print` resets both.

Both output formats live in `FORMATS` (43mm coin capsule, 4x5 per sheet; 40mm Avery
Zweckform L3415 label, 4x6 per sheet with screen-only alignment rings). `setFormat()`
switches the whole UI — the `--capsule-size` CSS variable, the headings/hints and the
sheet geometry — so a new format only needs an entry there, not new render code.

`loadCapsuleImage()` tries the same-origin `/.netlify/images` proxy first so canvases stay
exportable, then a CORS request, then a plain load. New cover CDN hosts must be added to
`remote_images` in `netlify.toml`, otherwise only the (canvas-tainting) fallbacks remain and
the PNG export stops working for those motifs.

## Conventions

- No comments beyond a handful marking non-obvious behavior (the category mapping, the data-flattening step).
- Cover images come from third-party CDNs with inconsistent CORS support — do not add `crossorigin` attributes to `<img>` tags that display them (it was tried and broke loading for most covers); `onerror` fallbacks to a placeholder are used instead. The canvas pipeline uses `crossOrigin` only on off-DOM `new Image()` objects, and only as a fallback behind the proxy.
- Keep everything in `index.html` unless the app grows enough logic to justify splitting files — there's no build step to wire up new files automatically.
