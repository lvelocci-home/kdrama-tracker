# My K-Drama Years 🌸

A personal K-drama journal and tracker. Part watchlist, part diary.

**Live app:** https://lvelocci-home.github.io/kdrama-tracker/

## What it does

- **My list** — every drama with title, type (Drama/Reality), status, star rating, categories, where I watched it, dates, a favorite heart, and a generous journal space for how each show made me feel.
- **Dashboard** — counts of watched / watching / want-to-watch, favorites, what I'm watching now, recent journal entries, and a breakdown of my most-watched categories.
- **Referrals** — shows people recommended to me, who recommended them, and why. One tap moves a referral onto my want-to-watch list. A red badge appears when new ones come in from the form.
- **Views & filtering** — gallery cards or sortable table; filter by type, status, category, rating, and service; search by title; sort by rating, date, or title.
- **Want to watch** — drag to reorder so I can line up what's next.
- **Progress** — track which episode I'm on for shows in progress, and mark rewatches.
- **CSV import** — paste or upload a combined watch history (Title, Type, Service, Status, Date Finished, Rating, Notes) and review before saving, with duplicate detection.
- **Share My List + Recommend form** — one live link friends can open to see my watched list **and** submit drama recommendations to me right from the page.

## How my data is saved

- Local cache in the browser (instant) + my own **Supabase Postgres** database via a tiny **Render** API service (cross-device sync).
- Changes save automatically and sync across my phone, tablet, and computer once Cloud Sync is set up in Settings.
- My data lives only in my browser and my Supabase project — nowhere else.
- Friends submitting recommendations via the share link append directly to my referrals; the next sync brings them to my app.

## Architecture

```
┌──────────────────────────┐        ┌────────────────────────┐
│  GitHub Pages            │        │  Render web service    │
│  index.html / share.html │ ──────▶│  server/index.js       │ ──▶ Supabase Postgres
│  (vanilla JS, no build)  │   API  │  (Express)             │
└──────────────────────────┘        └────────────────────────┘
```

- **Frontend:** single self-contained `index.html` + `share.html`. Hosted free on GitHub Pages.
- **Backend:** tiny Express + `pg` service in `server/`. Two tables auto-created (`app_state`, `shares`). Hosted free on Render.
- **Database:** Supabase Postgres (free tier, permanent storage — Render's own Postgres deletes after 30 days, don't use it).

## Backend setup (one time)

The app works locally with just the browser, but cross-device sync and the shareable referral form need the backend. Full step-by-step in [`server/README.md`](server/README.md). Quick version:

1. **Supabase** → New project → grab the **Transaction pooler** URI (port 6543) from Project Settings → Database → Connection string.
2. **Render** → New Web Service → connect this repo →
   - Root Directory: `server`
   - Build: `npm install`
   - Start: `npm start`
   - Env vars: `DATABASE_URL` (Supabase URI), `ALLOWED_ORIGIN` (`https://lvelocci-home.github.io`)
3. **In the app** → Settings → Cloud Sync → paste the Render URL and a long random private token → **Sync now**. Use the same URL + token on every device.

Render's free tier sleeps after ~15 min idle — the first request takes 30-60s to wake.

## Updating

Edit `index.html` (or `share.html`) and push to `main`. GitHub Pages redeploys automatically (~1 minute).
For server changes, Render auto-deploys on push if connected; otherwise trigger a manual deploy from the Render dashboard.

---

*Made for me, by me (with a little help). No ads, no upsells, no nagging.* 💛
