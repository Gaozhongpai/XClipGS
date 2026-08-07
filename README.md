# XClipGS — Project Page

Project page for **XClipGS: Exact Half-Space Clipping for Medical Volume Gaussian Splatting**.

Live at: https://gaozhongpai.github.io/XClipGS/

## Layout

- `index.html` — the page (Academic Project Page / Nerfies template + NDSplat theme, matching the 6DGS / 7DGS / Render-FM pages).
- `static/` — CSS/JS theme, figures (`images/`), demo videos (`videos/`), paper PDF (`pdfs/`).
- `demo/` — self-contained interactive WebGL clip-operator demo (PlayCanvas engine vendored; runs offline, no build step).

## Before publishing

- [ ] Confirm the **author list** in `index.html` (currently copied from the Render-FM page as a placeholder).
- [ ] The paper is under double-blind review — keep the repo/page private until the anonymity period allows posting.
- [ ] When the arXiv preprint is up: enable the arXiv button and replace the BibTeX stub.

## Serve locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```
