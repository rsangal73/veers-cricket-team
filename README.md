# Veers Cricket Team

Website for the Veers Cricket Team — a hard tennis ball cricket team of 25 veteran
players (ages 40-60) based in West Windsor, NJ, founded in 2020.

Live at **[veerscricket.com](https://veerscricket.com)**.

## Site sections

- **About** — team story and quick stats
- **Squad** — player roster
- **Ground** — home ground details (Conover Field, West Windsor)
- **Sponsors** — proud sponsor: [Nearsite](https://www.nearsite.com/)
- **Contact** — contact info and practice/matchday schedule

## Stack

Single-file static site (`index.html`) with no build step — it's a pre-bundled
React app plus a small vanilla-JS snippet (appended before `</body>`) that injects
the Sponsors section and its nav links after the app mounts.

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
- `logo.png`, `veers_v_transparent.png` — team logo assets
- `wrangler.toml` — Cloudflare Workers config
- `.assetsignore` — asset upload exclusions
- `_headers` — Cloudflare static-hosting cache rules
