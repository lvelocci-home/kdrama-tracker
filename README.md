# My K-Drama Years 🌸

A personal K-drama journal and tracker. Part watchlist, part diary.

**Live app:** https://lvelocci-home.github.io/kdrama-tracker/

## What it does

- **My list** — every drama with title, type (Drama/Reality), status, star rating, categories, where I watched it, dates, a favorite heart, and a generous journal space for how each show made me feel.
- **Dashboard** — counts of watched / watching / want-to-watch, favorites, what I'm watching now, recent journal entries, and a breakdown of my most-watched categories.
- **Referrals** — shows people recommended to me, who recommended them, and why. One tap moves a referral onto my want-to-watch list.
- **Views & filtering** — gallery cards or sortable table; filter by type, status, category, rating, and service; search by title; sort by rating, date, or title.
- **Want to watch** — drag to reorder so I can line up what's next.
- **Progress** — track which episode I'm on for shows in progress, and mark rewatches.
- **CSV import** — paste or upload a combined watch history (Title, Type, Service, Status, Date Finished, Rating, Notes) and review before saving, with duplicate detection.
- **Share My List** — generates a standalone read-only page of my watched list to send to friends, no login required.

## How my data is saved

- Everything is stored in **my own Google Drive** (via the Drive API, in the app's private appData folder) plus a local cache in the browser.
- Changes save automatically and sync across my phone, tablet, and computer.
- My data is mine — it only ever lives in my Drive and my browser, nowhere else.

## Tech

A single self-contained `index.html` — no build step, no framework, no backend. Hosted free on GitHub Pages. Google sign-in uses Google Identity Services for Drive sync.

## Updating

Edit `index.html` and push to `main`. GitHub Pages redeploys automatically (~1 minute).

---

*Made for me, by me (with a little help). No ads, no upsells, no nagging.* 💛
