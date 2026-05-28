# The Shed

Tiny static page with two embedded YouTube videos. The QR code (`qr-code.svg` / `qr-code.png`) is meant to be laser-engraved on a sign and points to:

**https://theswedishmaker.github.io/the-shed/**

---

## 1. Swap in the real YouTube video IDs

Open `index.html` and find the two `REPLACE_VIDEO_ID_*` strings. Replace each with the 11-character ID from the YouTube URL.

Example: for `https://www.youtube.com/watch?v=dQw4w9WgXcQ` the ID is `dQw4w9WgXcQ`.

There are two spots:
- `REPLACE_VIDEO_ID_1` — Pierre's video
- `REPLACE_VIDEO_ID_2` — friend's video

You can also tweak the section titles in the `<h2>` tags while you're in there.

## 2. Publish to GitHub Pages

From this folder:

```bash
git init
git add .
git commit -m "Initial shed page"
git branch -M main
gh repo create the-shed --public --source=. --remote=origin --push
gh api -X POST repos/theswedishmaker/the-shed/pages -f source[branch]=main -f source[path]=/
```

The last line turns Pages on. Within ~1 minute the site is live at the URL above.

(If you don't have `gh` set up, create the repo manually on github.com, push with `git remote add origin … && git push -u origin main`, then enable Pages under Settings → Pages → Source: `main` / `/ (root)`.)

## 3. The QR code

- `qr-code.svg` — vector, use this for the laser
- `qr-code.png` — 900×900 raster, use for previews / web

Both encode the URL above with error correction level **H** (≈30% redundancy), so they stay scannable even if the engraving picks up scratches or a knot in the wood eats some modules.

The 4-module "quiet zone" border around the code is part of the spec — don't crop it off, or scanners will struggle.
