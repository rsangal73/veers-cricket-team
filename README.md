# Veers Cricket Team - GitHub + Cloudflare Auto Deploy

This repo auto-deploys to Cloudflare Pages on every push to main.

## Setup Steps (One time - 3 mins)

### 1. Create GitHub Repo
- Go to github.com/new
- Name: `veers-cricket-team`
- Public or Private
- Create repo

### 2. Push this code
```bash
git init
git add .
git commit -m "Initial deploy - Veers Cricket Team - transparent logo, navy black jersey"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/veers-cricket-team.git
git push -u origin main
```

### 3. Get Cloudflare Credentials
- Cloudflare Dashboard -> My Profile -> API Tokens -> Create Token -> Edit Cloudflare Workers (or use custom with Pages:Edit, Account:Read)
- Copy Token
- Dashboard -> Right sidebar -> Account ID -> Copy

### 4. Add GitHub Secrets
Go to GitHub Repo -> Settings -> Secrets and variables -> Actions -> New repository secret
Add:
- `CLOUDFLARE_API_TOKEN` = your token
- `CLOUDFLARE_ACCOUNT_ID` = your account ID

### 5. Create Cloudflare Pages Project (first time)
- Cloudflare Dashboard -> Pages -> Create Project -> Connect to Git -> Select your repo
- Build settings: Framework preset = None, Build command = empty, Output directory = /
- Deploy - then future deploys will be handled by GitHub Action

### 6. Done!
Now every `git push` auto-deploys.

## Local dev
Just open index.html - it's a single file static site, no build needed.

## Files
- index.html - main site
- logo.png / veers_v_transparent.png - transparent logo
- .github/workflows/deploy.yml - auto deploy
