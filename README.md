# Veers Cricket Team

Website for the Veers Cricket Team — a hard tennis ball cricket team of 25 veteran
players (ages 40-60) based in West Windsor, NJ, founded in 2020.

Live at **[veerscricket.com](https://veerscricket.com)**.

## Site sections

- **About** — team story and quick stats
- **Squad** — player roster
- **Ground** — home ground details (Conover Field, West Windsor)
- **Matches** — recent match results with CricClubs scorecard links (see below)
- **Sponsors** — proud sponsor: [Nearsite](https://www.nearsite.com/)
- **Gallery** — [separate page](https://veerscricket.com/gallery/) with match/party photos
- **Contact** — contact info and practice/matchday schedule

## Stack

Single-file static site (`index.html`) with no build step — it's a pre-bundled
React app plus a small vanilla-JS snippet (appended before `</body>`) that injects
the Matches and Sponsors sections and all extra nav links after the app mounts.
`gallery/index.html` is a separate, lightweight hand-written page (no React
bundle) for the photo gallery.

## Updating match results (no code needed)

Match links live in a Google Sheet, not in the code. To publish a new result:

1. Open the team's "Veers Matches" Google Sheet.
2. Add a row with columns: `Date`, `Opponent`, `Result`, `Scorecard Link`
   (paste the CricClubs scorecard URL here).
3. That's it — the site fetches the sheet live, so the match shows up on
   veerscricket.com within seconds, sorted newest-first. No GitHub, no deploy.

One-time setup (already done if `MATCHES_SHEET_ID` in `index.html` is filled
in): create the sheet with those exact column headers, share it as
"Anyone with the link — Viewer", and put its ID (the long string in the
sheet's URL between `/d/` and `/edit`) into the `MATCHES_SHEET_ID` constant
near the top of the appended `<script>` in `index.html`.

## Adding gallery photos (no code needed)

See [`gallery/photos/README.md`](gallery/photos/README.md) — upload photos via
GitHub's web UI, add a matching entry to `gallery/manifest.json`, done.

## Deployment

Hosted on **Cloudflare Workers (static assets)**, connected directly to this
GitHub repo via Cloudflare's Git integration. Every push to `main` triggers an
automatic build and deploy — no GitHub Actions or secrets involved.

- `wrangler.toml` — declares the static assets directory and SPA fallback
- `.assetsignore` — excludes `.git`, config files, and docs from the deployed
  asset bundle
- `_headers` — cache-control rules for the deployed assets
- Custom domain `veerscricket.com` is bound to the Worker in the Cloudflare
  dashboard

## Local dev

Just open `index.html` directly in a browser — it's a single file, no build
needed.

## Files

- `index.html` — the site
- `gallery/index.html` — the photo gallery page
- `gallery/manifest.json` — list of gallery photos (edit this to add photos)
- `gallery/photos/` — the actual photo files
- `logo.png`, `veers_v_transparent.png` — team logo assets
- `wrangler.toml` — Cloudflare Workers config
- `.assetsignore` — asset upload exclusions
- `_headers` — Cloudflare static-hosting cache rules
- `robots.txt`, `sitemap.xml` — search engine crawling config
