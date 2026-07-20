# How to add photos

Photos are organized in one subfolder per event/category, e.g.
`gallery/photos/TeamEvent_July9_2026/`.

1. On GitHub, open this `gallery/photos/` folder. For a new event, create a
   new subfolder by uploading straight into a new path (see step 2). For an
   existing event, open its subfolder.
2. **Add file → Upload files** → drag in your photos for that event (or drag
   the whole event folder from your computer — GitHub preserves the folder
   structure) → commit directly to `main`.
3. Open `gallery/manifest.json` (two levels up) → **Edit** → add one entry
   per photo you just uploaded:

   ```json
   {
     "file": "/gallery/photos/TeamEvent_July9_2026/TeamEvent_July9_2026_1.jpg",
     "caption": "Optional caption shown in the lightbox",
     "album": "Team Event — July 9, 2026"
   }
   ```

   - `file` — path to the photo you uploaded, including its subfolder
   - `caption` — shown under the photo in the lightbox (optional)
   - `album` — groups photos under a heading on the gallery page; use the
     same album name for every photo from the same event (optional — omit
     it and photos just show in one list)

4. Commit. The site auto-deploys and the new photos show up at
   [veerscricket.com/gallery](https://veerscricket.com/gallery/) within a
   minute or two.

Tip: keep photos under ~2MB each (resize/compress before uploading) so the
gallery page stays fast to load.
