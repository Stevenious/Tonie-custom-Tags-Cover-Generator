# TonieCover 43mm

A single-page tool for creating print-ready covers for Tonie custom tags — 43mm coin capsules or 40mm Avery Zweckform L3415 labels — used with the [Toniebox](https://tonies.com). Search the public Tonies catalog for a title, fine-tune its cover art (zoom, rotation, position, background color, optional curved text), and collect covers on an A4 print sheet sized for real 43mm capsules.

## How it works

- **Search** — on load, the app fetches the community-maintained [tonies-json](https://github.com/toniebox-reverse-engineering/tonies-json) catalog (~6,500 titles) directly from the browser and normalizes it into a flat list with title, series, category, and cover image.
- **Editor** — the right-hand panel renders a live, actual-size 43mm preview. Drag the image directly, or use the zoom/rotation/offset sliders, background color picker, and cutting-guide style. An optional text ring can be curved around the capsule edge.
- **Own images** — the upload button accepts any local image file as a custom cover for titles missing from the catalog.
- **Print sheet** — covers added to the sheet are laid out in a 4-column A4 grid at true 43mm size; the browser's print dialog (set to 100% / actual size) produces a page ready to cut out and insert into coin capsules.
- Everything runs client-side — no accounts, no server-side storage. The print sheet only persists for the current browser session.

## Tech

Plain HTML/CSS/JS — no build step. Styling via the Tailwind CSS CDN build, icons via Font Awesome, font via Google Fonts. A `manifest` and a minimal service worker are injected at runtime (via Blob URLs) so the page can be added to an iOS/Android home screen as a lightweight PWA.

## Running locally

This is a static site — any static file server works:

```bash
netlify dev
```

or simply open `index.html` in a browser.

## Deployment

`netlify.toml` publishes the project root as-is; there is no build command.
