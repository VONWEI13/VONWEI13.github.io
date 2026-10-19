# VONWEI13.github.io

Personal academic homepage of **Wei Feng（冯惟）** — Ph.D. candidate, Department of Computer Science and Technology, Tsinghua University.

A single static page with two switchable skins, no framework and no build step:

- **Normal** — light sidebar layout (default)
- **Terminal** — dark, monospace, terminal-window sections

Toggle with the button at the bottom-right corner; the choice persists in `localStorage`, and `/#terminal` opens the dark skin directly.

Live at **https://vonwei13.github.io/** — GitHub Pages serves this repo as-is (`.nojekyll`).

## Structure

```
index.html    the entire site — both themes, content, and styles
assets/       avatar.jpg · boardgame2025_half.png
.nojekyll     serve files as-is, skip Jekyll
.github/workflows/google_scholar_crawler.yaml   daily Google Scholar crawl
google_scholar_crawler/                         crawler script used by the action
```

The crawler writes citation stats to the `google-scholar-stats` branch once a day (08:00 UTC) and on every push. The current page does not render them yet; the data is there if citation badges are ever wanted.

## Publishing changes

```bash
git add -A && git commit -m "update" && git push
```

The site refreshes a minute or so after pushing to `main`.

## Everyday maintenance — index.html

Each section exists **twice** (`.v5-*` for Normal, `.v3-*` for Terminal). Keep both in sync:

- **News** — add an `<li>` at the top of the `v5-news` / `v3-news` lists.
- **New paper** — copy a `.v5-pub` block (venue badge first, then title link + authors) in Publications, and the matching `.v3-row` in the Terminal theme. "Other Academic Contributions" follows the same format.
- **Awards** — one line per award in `v5-honors` / `v3-honors`.
- **Stats bar (Terminal)** — counts are hand-maintained: Scholarly Works / 1st-Author / Paper Awards / Patents.

## Local preview

```bash
python3 -m http.server 8000   # open http://localhost:8000
```

Opening `index.html` via file:// also works; web fonts come from Google Fonts CDN.
