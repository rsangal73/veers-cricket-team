# How to add photos

1. On GitHub, open this `gallery/photos/` folder → **Add file → Upload files** →
   drag in your match/party photos → commit directly to `main`.
2. Open `gallery/manifest.json` (one level up) → **Edit** → add one entry per
   photo you just uploaded:

   ```json
   {
     "file": "/gallery/photos/2026-07-18-vs-somewhere-1.jpg",
     "caption": "Veers vs Somewhere CC — Jul 18, 2026",
     "album": "vs Somewhere CC — Jul 18, 2026"
   }
   ```

   - `file` — path to the photo you uploaded (must start with `/gallery/photos/`)
   - `caption` — shown under the photo in the lightbox (optional)
   - `album` — groups photos under a heading on the gallery page (optional —
     omit it and photos just show in one list)

3. Commit. The site auto-deploys and the new photos show up at
   [veerscricket.com/gallery](https://veerscricket.com/gallery/) within a
   minute or two.

Tip: keep photos under ~2MB each (resize/compress before uploading) so the
gallery page stays fast to load.
