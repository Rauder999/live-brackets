# LiveBrackets

Free live tournament brackets for THE FINALS communities. Built by
[CODEBREAKERS](https://github.com/Rauder999/codebreakers-bracket) and shared
with smaller servers that just want working brackets — no bot, no analytics,
no setup.

**Admin app:** https://rauder999.github.io/live-brackets/
**Live viewer:** https://rauder999.github.io/live-brackets/live.html

## What you get

- Bracket builder for 2–32 teams: single or double elimination, 4-team
  cash-out pods (THE FINALS style), optional head-to-head finals bracket,
  best-of-3 grand final that unfolds game by game.
- **Live page** that syncs in real time — share one link with your community,
  results appear the moment the organizer clicks them.
- Team rosters with hover tooltips, seeding, CSV / Google Sheets import,
  mid-tournament substitutions (Teams button), undo/redo, co-host links so a
  second organizer can help run the bracket.
- Archives: freeze a finished tournament into a permanent read-only page.
- OBS overlay (`overlay.html`) with a transparent background for streams.
- PNG export.

## Getting access

Organizer accounts are invite-based. Ask Rauder for an invite code, then open
the admin app → **Sign in / Register**. Everything your account creates is
yours alone — other communities can't see or touch it.

## Repository layout

This repo is the deployed site (GitHub Pages): `index.html` + `assets/` are
the built admin app, `live.html`/`overlay.html` are self-contained viewers,
`client/` is the React/TypeScript source and `worker/` is the Cloudflare
Worker backend (sessions, accounts, archives).

Build: `npm install && npm run build`, copy `dist/public/index.html` and
`dist/public/assets/*` to the repo root, push. Worker: `cd worker && npx
wrangler deploy`.
