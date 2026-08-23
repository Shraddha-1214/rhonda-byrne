# The Architecture of Belief

An interactive, single-page editorial dossier on Rhonda Byrne — from a $2 million production debt and her father's death, to *The Secret* and its two-decade afterlife.

Static HTML/CSS/JS. No build step, no dependencies to install, no backend.

**[Live demo →](#)** *(add your Vercel URL here after deploying)*

---

## What's inside

- **The Ledger** — 18 verified biographical milestones (1951–2026), filterable by Career / Film Production / Philosophy / Books, with a year-scrubber slider and colour-coded tone (crisis / manifestation-era / non-duality)
- **75 Questions, Five Acts** — an original interview-prep architecture with live search, per-act filtering, and one-click "copy for notes"
- **Media Vault** — 8 primary/verifying sources with working links (Wikipedia, TIME, IMDb, HarperCollins, Salon, and Byrne's own recent interviews)
- **Reel Concepts** — two short-form topic maps for editors (hooks + beats, not scripted dialogue)

## Tech stack

| Layer | Choice |
|---|---|
| Markup | Semantic HTML5 |
| Styling | Tailwind CSS (via CDN Play script) + a small custom stylesheet for the type system, colour tokens, and bespoke components (ledger timeline, question cards, progress bar) |
| Fonts | Newsreader (display serif), Plus Jakarta Sans (body), JetBrains Mono (data/citations) — loaded from Google Fonts |
| Interactivity | Vanilla JavaScript, no framework |

Everything lives in one HTML file — data (timeline, questions, sources), markup, styles, and behaviour. There's nothing to `npm install`.

## Project structure

```
.
├── index.html      # the entire app
└── README.md
```

If you're starting from the file this was generated as (`architecture-of-belief.html`), just rename it to `index.html` before pushing — that's what makes zero-config static hosting work.

## Run it locally

No tooling required — just open the file:

```bash
open index.html          # macOS
# or
python3 -m http.server    # then visit http://localhost:8000
```

## Deploy to Vercel

**Option A — Vercel dashboard (easiest)**
1. Push this repo to GitHub.
2. Go to [vercel.com/new](https://vercel.com/new) and import the repo.
3. Framework preset: choose **Other**. Leave the build command empty and the output directory as `./`.
4. Deploy. Vercel serves `index.html` at the root automatically.

**Option B — Vercel CLI**
```bash
npm i -g vercel
vercel        # first deploy, follow the prompts
vercel --prod # promote to production
```

No `vercel.json` is required for a single static HTML file at the repo root. If you keep the file under a subfolder (e.g. `/public/index.html`), add:

```json
{
  "outputDirectory": "public"
}
```

## Editing the content

Everything is driven by three arrays near the top of the `<script>` block:

- `TIMELINE` — one object per milestone (`year`, `category`, `tone`, `title`, `body`)
- `QUESTIONS` — one object per prompt (`id`, `act`, `pause`, `text`)
- `SOURCES` — one object per citation card (`pub`, `badge`, `title`, `note`, `url`)

Add, remove, or reorder entries in these arrays and the UI (filters, search, counts) updates automatically — no other code changes needed.

## A note on sourcing and content

Biographical claims are drawn from public reporting and reference sources linked in the Media Vault section (Wikipedia, IMDb, TIME, Salon, HarperCollins/HarperOne, thesecret.tv, and Byrne's own recent interviews). Figures that vary across outlets — such as the number of people interviewed for the original film — are presented as ranges rather than false precision.

The 75 interview questions are original editorial prompts written for a hypothetical long-form conversation. They are **not** transcript excerpts, and no answers are attributed to Rhonda Byrne anywhere in the piece.

This is an independent editorial project and is not affiliated with, endorsed by, or produced in partnership with Rhonda Byrne, Prime Time Productions, HarperCollins, or any other rights holder mentioned.

## License

Code (HTML/CSS/JS) in this repo: use it, fork it, adapt it. The biographical content is original editorial writing based on the cited public sources — if you reuse the written content elsewhere, keep the sourcing note above attached.
