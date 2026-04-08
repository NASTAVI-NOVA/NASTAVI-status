# NASTAVI Status

Live uptime monitoring and status page for [nastavi.co](https://nastavi.co).

**Status page:** https://status.nastavi.co

## What's monitored

| Monitor | URL |
|---|---|
| NASTAVI Platform | https://nastavi.co |
| API & Database | https://nastavi.co/api/health |
| Artist Dashboard | https://nastavi.co/dashboard |
| Marketplace | https://nastavi.co/marketplace |
| Pricing | https://nastavi.co/pricing |

## How it works

- GitHub Actions checks each URL every hour and commits results to this repo
- The `/api/health` endpoint pings the Supabase database and Backblaze B2 storage — returns 503 if either is degraded
- Incident history is stored as Markdown files and GitHub Issues
- The status page is deployed automatically to GitHub Pages

## Setup

See `.upptimerc.yml` for configuration. Secrets required in GitHub repo settings:

- `GH_PAT` — GitHub Personal Access Token with `repo` scope (allows Actions to commit results back)

Optional notification secrets:
- `NOTIFICATION_SLACK` — Slack webhook URL
- `NOTIFICATION_EMAIL` — Comma-separated email addresses

## DNS

Point a CNAME record for `status.nastavi.co` to `nastavi-nova.github.io`.
