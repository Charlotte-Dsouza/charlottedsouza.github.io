# charlottedsouza.github.io

Personal portfolio: Charlotte D'Souza, Brand & Media Marketing, EMEA.

Single static page. No build step, no dependencies, no framework. Edit `index.html` and push.

---

## Publishing it

1. Create a GitHub repo named exactly **`charlottedsouza.github.io`** (swap in your own username). Naming it this way gives you `https://charlottedsouza.github.io` rather than a `/repo-name` sub-path.
2. Upload `index.html` and this `README.md` to the root of the repo.
3. Go to **Settings > Pages**. Under *Build and deployment*, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
4. Wait 1 to 2 minutes. The site is live at `https://charlottedsouza.github.io`.

For a custom domain later, add it under Settings > Pages > Custom domain and add a `CNAME` file containing just the domain.

---

## Adding the Cake the Collective video

GitHub Pages will serve a video file, but a `.mov` will not play in most browsers and the files are usually far too big. Convert it first.

**Step 1: convert to MP4.** MP4 with H.264 video and AAC audio plays everywhere.

Easiest route, no software: use CloudConvert or HandBrake (free, desktop). In HandBrake, pick the "Fast 1080p30" preset and set the format to MP4.

If you have ffmpeg installed, one command does it:

```
ffmpeg -i cake.mov -vcodec libx264 -crf 26 -preset slow -vf "scale=1280:-2" -acodec aac -b:a 128k -movflags +faststart cake-picnic.mp4
```

`-crf 26` controls quality: lower is better quality and a bigger file, higher is smaller. `-movflags +faststart` matters, it lets the video start playing before it has fully downloaded.

**Step 2: check the size.** Aim for under 20 MB. GitHub's hard limit is 100 MB per file, but anything over about 25 MB makes the page feel slow on mobile. If it is too big, raise the `-crf` number, shorten the clip, or drop the resolution to 720 with `scale=1280:-2` becoming `scale=854:-2`.

**Step 3: make a poster image.** A still frame shown before the video loads. Take a screenshot, or:

```
ffmpeg -i cake-picnic.mp4 -ss 00:00:02 -vframes 1 cake-poster.jpg
```

**Step 4: add the files.** Create a folder called `media` in the repo and put `cake-picnic.mp4` and `cake-poster.jpg` inside it. The `<video>` block already in `index.html` points at exactly those paths, so nothing else needs changing. Delete the red placeholder note next to it.

The `<video>` tag also lists a `.webm` source. That is optional. If you generate one it will be used by browsers that prefer it, and if you do not, the MP4 is used and nothing breaks.

**If the video is very large or you would rather not host it:** upload it to YouTube as unlisted, then replace the whole `<figure class="filmstrip">` block with a link, or an iframe embed.

---

## Before you publish, checklist

- [ ] Search the file for `PLACEHOLDER` and resolve each one. They render as red dashed boxes so you cannot miss them.
- [ ] Add `Charlotte_Dsouza_CV.pdf` to the repo root. Two links point at it, and until it exists both 404.
- [ ] **Clear the case study figures.** The page carries no competitor data, no licensed panel data, no budgets and no agency reports. It does carry internal outcome figures: percentage-point Top-of-Mind movements, partner order growth, GMV growth, and how many markets cleared the campaign health framework. Check these against your employer's confidentiality policy before going live, and remove anything that is not comfortable in public.
- [ ] The India entry sits in the "campaign planning and execution" group and reflects the PR Pundit portfolio work rather than media planning. Decide whether that reads honestly to you.
- [ ] The MENA case study still names talabat alongside HungerStation, while the markets grid now shows KSA only. Align the two before publishing.

---

## Editing notes

**Adding a case study.** Copy any `<article class="case">` block. Each has a coloured `strip`, a `tag`, an `h3`, and a `<dl>` of Situation, What I did, Result. Pick the strip colour from the CSS variables at the top: `--bar-magenta`, `--bar-blue`, `--bar-green`, `--bar-cyan`, `--bar-yellow`, `--bar-red`.

**Adding a playbook or analysis.** Copy a `<div class="art">` block in the Playbooks section. Three per row on desktop, so add in threes if you want a tidy grid.

**Adding a market.** Copy a `<div class="mk">` block. The `lvl` bar colour encodes depth: magenta for strategy and budget owned, blue for planning and execution, cyan for support and governance. Keep the order grouped by colour, the legend above depends on it reading cleanly.

**Removing a placeholder.** Delete the whole `<span class="todo">...</span>` line.

**Colours and type** are CSS variables in `:root` at the top of the file. Change them there and the whole page follows. Dark mode is automatic via `prefers-color-scheme`.

---

## Design notes

The palette comes from broadcast test-card colour bars, desaturated, a nod to the ATL and TV side of the work. The bars run across the top and bottom of the page and reappear as the depth indicator in the markets grid and the spine of each case card.

The hero holds a brand-tracker line rather than a headline statistic, because the tracker is the artefact this job actually revolves around. It is indexed and unlabelled on purpose.

Type: Bricolage Grotesque for display, Inter for body, IBM Plex Mono for labels and data.

Accessible by default: keyboard focus rings, `prefers-reduced-motion` respected, responsive down to mobile, and the SVG carries a text alternative.
