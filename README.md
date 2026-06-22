# music-site

Landing page for Henry Solberg (milkshakeiii) — synth-driven music for sci-fi
worlds, available for sync licensing, custom scoring, and commissions.

A single static page (`index.html`) with an in-browser audio player for four
demo tracks in `audio/`. No build step.

## Hosting

Served by GitHub Pages from the `main` branch root, at the custom domain
**https://henryscifimusic.com** (the `CNAME` file binds it). DNS is managed in
Google Cloud DNS under the GCP project `henryscifimusic`; the domain is
registered via Cloud Domains / Squarespace.

To preview locally, open `index.html` in a browser, or run a quick static
server from this folder:

```
python -m http.server 8000
```

then visit http://localhost:8000.

## Editing

- Contact email, copy, and track titles live in `index.html`.
- Replace the demo MP3s in `audio/` (keep the same filenames, or update the
  `data-src` attributes on each `.track` in `index.html`).
