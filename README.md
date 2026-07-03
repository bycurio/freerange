# FREE RANGE — Egg Hunt · Level 3 Build

First-person open-world egg hunt. One `index.html`, plus an `/assets` folder of
real CC0 assets that upgrade the graphics. **Every asset is optional** — the game
runs immediately with built-in procedural fallbacks, and each file you add
upgrades that element automatically. The start screen shows a status line
(`sky ✓ · chicken ✓ · ground — …`) so you can see exactly what loaded.

---

## 1 · Get it live (2 minutes, works before adding any assets)

1. Create a repo (or use your existing GitHub Pages repo, e.g. `jonplu.github.io`).
2. Upload this folder's contents: `index.html` + the `assets/` folder.
3. If it's a new repo: Settings → Pages → Deploy from branch → `main` → root.
4. Your game is at `https://<username>.github.io/<repo>/` (or
   `https://jonplu.github.io/free-range/` if you put it in a `free-range` folder
   of your existing Pages repo).

**Webflow embed** — one Embed element on a blank page:

```html
<iframe src="https://jonplu.github.io/free-range/"
  style="position:fixed;inset:0;width:100%;height:100%;border:0"
  allow="fullscreen; autoplay; pointer-lock" allowfullscreen></iframe>
```

---

## 2 · The asset shopping list (all free, all CC0 — no credit required)

Download each, rename **exactly** as shown, drop into `assets/`, commit. Refresh
the game and watch the status line.

| File | What it upgrades | Where to get it |
|---|---|---|
| `sky.hdr` | Photographic sky + realistic light on everything (biggest single upgrade) | [polyhaven.com/hdris](https://polyhaven.com/hdris) → pick a warm one (search "sunset" or "golden") → download **2K · HDR** |
| `grass.jpg` | Real photoscanned ground | [ambientcg.com](https://ambientcg.com) → search **Grass001** → 2K-JPG zip → use `Grass001_2K_Color.jpg` |
| `grass_n.jpg` | Ground surface detail (bumps in the light) | Same zip → use `Grass001_2K_NormalGL.jpg` |
| `wood.jpg` | Coops, bridges & ramps get real timber | ambientcg → search **Planks** (e.g. Planks023) → 2K-JPG → the `_Color.jpg` |
| `chicken.glb` | Real modelled chicken, with skeletal animation if the model has it | [quaternius.com](https://quaternius.com) → Animal packs (CC0) → chicken → GLB. Or [sketchfab.com](https://sketchfab.com) → search "chicken", filter **Downloadable + CC0** → glTF/GLB |
| `tree.glb` | Real trees replace the low-poly ones (same positions) | quaternius.com tree packs, or any CC0 tree GLB |

Notes:
- **Any** sky HDR, ground texture, or chicken GLB works — those names are just
  reliable known-good picks. 2K resolution is the sweet spot; 4K works but loads slower.
- The chicken is auto-scaled, auto-grounded, and its animation clips are
  auto-detected (it looks for names containing walk/run/move/idle, else plays
  the first clip). If your chicken walks backwards, open `index.html` and set
  `CHICKEN_YAW_OFFSET = Math.PI;` near the asset system section.
- GLB must be uncompressed (no Draco). Quaternius GLBs are fine as-is.

## 3 · Status line legend

`✓` loaded and applied · `—` file not found (fallback in use) · `✕` file found
but failed to apply (bad format — try a different one)

## 4 · Tuning

All gameplay dials are constants at the top of the script in `index.html`:
difficulty curve (`difficulty()`), chicken speeds (`HUNT_SPEED`, `HUNT_CAP`),
detection (`SIGHT_BASE`), boost (`BOOST_*`), coop hatching (`HATCH_COUNT`,
`COOP_CD_MS`), and spawn pacing (`spawnClock` in the main loop).

Sounds stream from `jonplu.github.io/sound/` — swap the three `<audio>` tags
to change the music.
