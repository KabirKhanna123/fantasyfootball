# Dhoom Draft HQ

A static site consolidating all the draft tools onto one home page with
clean navigation. No build step, no backend — every page is the exact same
self-contained HTML file you already had, just organized and linked together.

## Structure

```
fantasy-site/
├── vercel.json          Vercel config (clean URLs — /draft-kabir instead of /draft-kabir.html)
└── public/
    ├── index.html                Home page / menu
    ├── draft-kabir.html          Kabir — live draft assistant (Dhoom)
    ├── draft-seher.html          Seher — live draft assistant (Dhoom)
    ├── draft-league.html         League-wide tool (any team, Dhoom)
    ├── draft-kabir-mock.html     Kabir — mock draft (auto-sim opponents)
    ├── draft-seher-mock.html     Seher — mock draft (auto-sim opponents)
    ├── draft-dagastani.html      Dagastani Glazer league — live draft assistant
    ├── full-simulation.html      Full 10-team, 16-round simulation
    └── monte-carlo.html          100,000-run Monte Carlo simulation
```

Each tool keeps its state entirely in your own browser (localStorage/in-memory) —
nothing here adds a server or database.

## Deploy to Vercel

**Option A — GitHub (recommended, auto-deploys on every push):**

1. Create a new GitHub repo and push this folder to it:
   ```
   cd fantasy-site
   git init
   git add .
   git commit -m "Dhoom Draft HQ"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new), click **Import** next to your repo.
3. Vercel auto-detects it as a static site — no config needed, just click **Deploy**.
4. Done. You get a URL like `dhoom-draft-hq.vercel.app`, and every future `git push` auto-deploys.

**Option B — Vercel CLI (deploy right now, no GitHub needed):**

```
npm i -g vercel
cd fantasy-site
vercel
```
Follow the prompts (log in, confirm the project). It'll give you a live URL immediately.

## Adding a tool later

Drop a new `.html` file into `public/`, add a card for it on `index.html`
(copy an existing `<a class="card">` block), and redeploy. That's the whole process —
no routing config to touch since `vercel.json` already handles clean URLs for any
file in `public/`.

## Custom domain

In the Vercel dashboard: your project → **Settings → Domains** → add your domain
and follow the DNS instructions Vercel gives you.
