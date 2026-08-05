# Profile Build Guide — supporting the README

This is the companion doc to `README.md`: the analysis, setup steps, and
recommendations that don't belong inside the README itself.

---

## 1. Analysis — what I found across your sources

**Resume:** strong, consistent story — Python/ML foundation + React/full-stack
range, one real ML internship, four solid projects, relevant certs. No major
inconsistencies between resume and GitHub.

**GitHub (`alphasuraj18`, 18 repos, 1 follower):**
- Two of your resume projects (`llm-flashcard-generator`,
  `FitHub-AI-Personalized-Fitness-Coach`) are public and correctly named — good.
- Your current "popular repos" on GitHub are dominated by smaller/older work:
  `Notepad` (Java clone), `Water-Quality-Test`, `Netflix-Movie-Recommendation-System`,
  `Netflix-homepage-clone`. These are fine as learning reps but **shouldn't be
  your public face** next to a Stock Price Predictor with 7 benchmarked models.
- I could not confirm public repos for **Stock Price Predictor** or **Quiz.io**
  from your resume — either they're private, unlisted among your 18, or named
  differently. Flagged as placeholders in the README; fix this first (see §5).
- Your GitHub bio is currently blank/minimal ("Hello I'm Suraj Kumar") — worth
  a one-line upgrade (see §7).

**LeetCode (`Surajkumar18`):** profile is set up but I can't pull your live
solve count/rating from here — the badge in the README (`leetcode-stats-two-omega`)
will render it live once the README is pushed to GitHub.

**Verdict:** you don't need new skills to look strong — you need your GitHub
*surface* (pins, repo names, bio, READMEs) to catch up to what's already on
your resume.

---

## 2. Banner prompt (for the header image, if you want a custom one instead of the gradient wave)

> A minimal, premium developer banner, 1584×396px. Deep navy-to-black
> background (#0F172A to #000000) with a subtle low-opacity circuit-board /
> neural-network line pattern in the corners. Centered, clean sans-serif
> typography reading "SURAJ KUMAR — Software Engineer" in soft cyan (#22D3EE)
> with a smaller subtitle "AI/ML · Full-Stack · Python" beneath it in muted
> white. A faint glassmorphism panel behind the text (blurred, low-opacity
> white rectangle with rounded corners). Small line-art icons — a neural
> node cluster, a bracket `</>` glyph, a subtle Python/React mark — placed
> sparingly at the far left and right edges, not cluttering the center. No
> rainbow gradients, no cartoon mascots, no stock-photo people. Flat,
> modern, dark, professional — the kind of banner a senior engineer's
> GitHub would have.

Generate this with any image tool you like (or skip it — the capsule-render
wave gradient already in the README needs zero extra assets and matches the
theme).

---

## 3. Folder structure

Your profile README lives in a special repo named **exactly** your username:

```
alphasuraj18/
└── alphasuraj18/              ← repo name MUST match your GitHub username
    ├── README.md               ← the file I generated
    ├── profile-banner.png      ← optional, only if you generate the custom banner
    └── .github/
        └── workflows/
            └── snake.yml       ← contribution snake animation (below)
```

If this repo doesn't exist yet: GitHub → **New repository** → name it
`alphasuraj18` → check "Add a README" → GitHub auto-detects it as your
profile repo and shows a banner confirming it.

---

## 4. Assets & external widgets used (all free, no API key required)

| Purpose | Service |
|---|---|
| Typing animation | readme-typing-svg.demolab.com |
| Profile view counter | komarev.com/ghpvc |
| Follower badge | img.shields.io |
| Header/footer wave | capsule-render.vercel.app |
| Stats card | github-readme-stats.vercel.app |
| Streak stats | github-readme-streak-stats.herokuapp.com |
| Top languages | github-readme-stats.vercel.app/api/top-langs |
| Activity graph | github-readme-activity-graph.vercel.app |
| Trophies | github-profile-trophy.vercel.app |
| LeetCode stats card | leetcode-stats-two-omega.vercel.app |
| Snake contribution animation | Platane/snk (GitHub Action, below) |
| Language/tool icons | devicon (jsdelivr CDN) + simpleicons.org |

All of these are actively maintained public widgets — no signup, no keys,
nothing to configure beyond swapping in your username (already done).

---

## 5. Setup instructions

1. Create/open the `alphasuraj18/alphasuraj18` repo (see §3).
2. Drop in `README.md` from this delivery, replace the default one.
3. **Before pushing:** fix the two placeholder project links —
   confirm or create public repos for **Stock Price Predictor** and
   **Quiz.io**, then swap the `github.com/alphasuraj18/...` placeholder
   URLs in the Featured Projects section for the real ones. Broken links
   are the #1 thing that makes a recruiter bounce.
4. Add `.github/workflows/snake.yml` (provided in §6) to enable the
   animated contribution snake — it needs zero configuration beyond
   being present in the repo; GitHub Actions runs it on a schedule.
5. Push. Within a minute the stats/streak/trophy/LeetCode cards render
   live — they're all read at request-time, not baked in.
6. Optional: generate the banner from §2 and swap the capsule-render
   header for `![banner](./profile-banner.png)` if you want something
   more custom than the gradient wave.

---

## 6. GitHub Actions workflow — contribution snake animation

Save as `.github/workflows/snake.yml` in your **profile repo**:

```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *"   # once a day
  workflow_dispatch: {}
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate snake animation
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push snake output to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Then in `README.md`, replace the `<!--START_SECTION:snake--> ... <!--END_SECTION:snake-->`
placeholder with:

```markdown
![snake animation](https://raw.githubusercontent.com/alphasuraj18/alphasuraj18/output/github-contribution-grid-snake-dark.svg)
```

(This image URL only resolves *after* the workflow runs once and creates
the `output` branch — it'll 404 until then, which is expected.)

---

## 7. Pinned repository recommendations

Pin exactly these four (GitHub → your profile → Customize your pins):

1. **FitHub-AI-Personalized-Fitness-Coach** — your strongest ML+product story
2. **llm-flashcard-generator** — most "now" tech (LLM API integration)
3. **Stock Price Predictor** (once public) — best signal of ML rigor (7-model comparison)
4. **Quiz.io** (once public) — your only pure frontend/React showcase, balances the ML-heavy rest

Leave `Notepad`, `Netflix-homepage-clone`, and similar clones unpinned —
keep them in the repo list for depth, but they shouldn't be first
impressions.

## 8. Improving weaker repositories

- **Notepad / Netflix-homepage-clone / Water-Quality-Test:** each needs a
  real README (one paragraph: what it does, stack, what you learned) —
  right now they read as untitled practice repos with no description.
  Either add a 10-minute README to each, or set them to private if they're
  purely tutorial-following exercises with no original contribution.
- **Netflix-Movie-Recommendation-System:** if this has real recommendation
  logic (collaborative filtering, content-based, etc.), it's actually
  resume-worthy — give it a proper README and consider swapping it in for
  Quiz.io as your 4th pin if Quiz.io's repo can't be confirmed public.

## 9. Overall GitHub profile suggestions

- **Bio:** change from "Hello I'm Suraj Kumar" to something like
  `Software Engineer · AI/ML & Full-Stack · Python, React, TensorFlow` —
  your bio shows up in search and hover-cards independent of the README.
- **Pin count:** you're at 18 repos with none currently pinned by choice —
  pinning the 4 above takes two minutes and immediately changes what a
  recruiter sees first.
- **Repo descriptions:** several of your public repos (including two of
  your popular ones) have no one-line description — add them; they show
  up right under the repo name in every listing.
- **Contribution consistency:** the streak/activity graphs in the README
  are a strength if you commit regularly and a weakness if you don't —
  if your graph is currently sparse, a small daily habit (even doc fixes)
  over the next few weeks will visibly change what recruiters see before
  you're actively applying.
