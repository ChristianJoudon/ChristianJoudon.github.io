# christianjoudon.github.io

My personal site — a multi-page portfolio served by GitHub Pages at
**https://christianjoudon.github.io**. Plain static HTML/CSS/JS, no build step.

## Structure

```
index.html                 Homepage (About, Experience, Work, Toolkit, Writing, Essays, Contact)
favicon.ico
Christian_Joudon_Resume.pdf
.nojekyll                  Tells GitHub Pages to serve files as-is (no Jekyll)
assets/
  site.css                Shared styling for every page
  site.js                 Sticky-header + scroll-reveal
  img/                    Project thumbnails (audio, covid, global, terran, uhnify)
work/                     10 project detail pages (each Work card links here)
essays/                   7 essay pages (each Essay row links here)
```

Every project card on the homepage opens its own page under `work/`, and every
essay opens its own page under `essays/`. Pages use relative links (`../assets/…`
from subpages, `assets/…` from the homepage), so the structure must stay intact.

## Editing & deploying

1. Edit the HTML directly (content is plain, readable markup).
2. Commit and push to the **`main`** branch — GitHub Pages serves from `main` at
   the repo root and updates within a minute.
3. Hard-refresh (Cmd+Shift+R) to clear the browser cache.

## Preview locally

Subpages use root-relative-style paths, so open them through a server, not by
double-clicking the file:

```
python3 -m http.server 8000
```

then visit http://localhost:8000.

## Adding project thumbnails

Four Work cards (Chime, HiTech Labs, Workflow Automation, Refund Builder) have no
image yet and render as text-only cards. To add one, drop a 16:9 JPEG in
`assets/img/` and add a `<div class="card-media">…</div>` block to that card in
`index.html` (and the matching `<figure class="detail-media">` on its `work/` page).
```
