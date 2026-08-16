# charlottedsouza.github.io

Personal portfolio — Charlotte D'Souza, Brand & Media Marketing, EMEA.

Single static page. No build step, no dependencies, no framework. Edit `index.html` and push.

---

## Publishing it

1. Create a GitHub repo named exactly **`charlottedsouza.github.io`** (swap in your own username). Naming it this way gives you `https://charlottedsouza.github.io` rather than a `/repo-name` sub-path.
2. Upload `index.html` and this `README.md` to the root of the repo.
3. Go to **Settings → Pages**. Under *Build and deployment*, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
4. Wait 1–2 minutes. The site is live at `https://charlottedsouza.github.io`.

To use a custom domain later (e.g. `charlottedsouza.com`), add it under Settings → Pages → Custom domain, and add a `CNAME` file containing just the domain.

---

## Before you publish — checklist

- [ ] Search the file for `PLACEHOLDER` and resolve every one. They render as red dashed boxes so you can't miss them on the page.
- [ ] Add `Charlotte_Dsouza_CV.pdf` to the repo root — two links point at it (hero and footer). Until it's there, both 404.
- [ ] Re-read the case studies against your employer's confidentiality policy. The page deliberately carries no competitor figures, no absolute tracker values and no research-vendor names. Keep it that way.
- [ ] Check the talabat / HungerStation market mapping in the Markets section.
- [ ] Decide whether to keep the India entry in the Markets grid (it's PR Pundit-era, not media).

---

## Editing notes

**Adding a case study.** Copy any `<article class="case">` block. Each has a coloured `strip`, a `tag`, an `h3`, and a `<dl>` of Situation / What I did / Result. Pick the strip colour from the CSS variables at the top (`--bar-magenta`, `--bar-blue`, `--bar-green`, `--bar-cyan`, `--bar-yellow`, `--bar-red`).

**Adding a market.** Copy a `<div class="mk">` block. The `lvl` bar colour encodes depth — magenta for strategy and budget owned, blue for planning and execution, cyan for support and governance. The legend above the grid explains it, so keep them consistent.

**Removing a placeholder.** Delete the whole `<span class="todo">…</span>` line.

**Colours and type** are all defined as CSS variables in `:root` at the top of the file. Change them there and the whole page follows. Dark mode is handled automatically via `prefers-color-scheme`.

---

## Design notes

The palette is drawn from broadcast test-card colour bars, desaturated — a nod to the ATL and TV side of the work. The bars run across the top and bottom of the page and reappear as the depth indicator in the markets grid and the spine of each case card.

The hero holds a brand-tracker line rather than a headline statistic, because the tracker is the artefact this job actually revolves around. It's indexed and unlabelled on purpose.

Type: Bricolage Grotesque for display, Inter for body, IBM Plex Mono for labels and data.

Accessible by default: keyboard focus rings, `prefers-reduced-motion` respected, responsive to mobile, and the SVG carries a text alternative.
