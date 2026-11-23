# music-site

Landing page for Henry Solberg (milkshakeiii) — synth-driven music for sci-fi
worlds, available for sync licensing, custom scoring, and commissions.

A single static page (`index.html`). No build step.

The "Selected work" section is **Many Worlds**: seven albums shown as a strip
of the watercolor world panels from the Many Worlds CD art.
Clicking a world opens it and plays that album's featured track; when a track
ends, the next world starts.

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

then visit http://localhost:8000. (Python's server can't seek within audio
files; seeking works on GitHub Pages.)

## Editing

- Contact email and copy live in `index.html`.
- Each world is an `<article class="world">` in `index.html`:
  - `data-src`: the MP3 in `audio/worlds/`
  - `data-track`: the track title shown in the player
  - `data-dur`: track length in seconds, shown until the file loads
  - `--pos` / `--mpos`: which part of the art shows in the narrow desktop
    strip / the mobile band
- Art: `img/worlds/*.jpg` (1024 × 1024, from the Many Worlds album panels) and
  `img/manyworlds.jpg` (the set cover).
- To change a world's featured track, encode it over the existing file, for
  example:

  ```
  ffmpeg -i "Star Pond.flac" -vn -map_metadata -1 -c:a libmp3lame -q:a 3 \
    -metadata title="Star Pond" -metadata artist="Henry Solberg" \
    -metadata album="The Enchanted Forest of Naibihpma" audio/worlds/enchanted-forest.mp3
  ```

  then update that world's `data-track` and `data-dur`.
