# CLAUDE.md

LiveBrackets — a stripped public fork of the CODEBREAKERS bracket tool
(`Rauder999/codebreakers-bracket`), given to smaller THE FINALS communities.
Live brackets only: the Discord bot, Notion import, Discord OAuth, stats and
the Start Tournament gate are removed on purpose. Do not re-add them here.

- Frontend: GitHub Pages, base path `/live-brackets/`. `index.html` + hashed
  bundle in `assets/` are built from `client/` (Vite); `live.html` and
  `overlay.html` are self-contained.
- Backend: Cloudflare Worker **livebrackets-api**
  (https://livebrackets-api.codebreakerstf.workers.dev), source in `worker/`.
  Own KV namespace and Durable Objects — fully isolated from the
  CODEBREAKERS deployment. Secrets: ADMIN_TOKEN (master), AUTH_SECRET.
- Multi-tenant: organizer accounts are minted with invite codes
  (master-only POST /invites); each account only sees its own sessions and
  archives.
- The bracket engine (`client/src/lib/bracketEngine.ts`) is shared source
  with the parent repo — port engine fixes from there manually when needed.
  The worker imports it directly, so redeploy the worker after engine edits.

Deploy: `npm run check` → `NODE_ENV=production npm run build` → copy
`dist/public/index.html` and new `dist/public/assets/*` bundle to the repo
root (delete the stale hashed bundle) → push to `main` (Pages auto-deploys).
Worker: `cd worker && npx wrangler deploy`.
