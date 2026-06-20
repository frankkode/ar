# Living Print — AR module (MindAR image tracking)

Point a phone/tablet camera at the printed figure (`marker.png`, "Figure 4.2")
and a beating 3D heart appears anchored to the page. Tap the heart to hear a
short narration. Reuses the same `heart.glb` as the VR scene.

## Files
- `index.html` — the AR app (A-Frame + MindAR + aframe-extras)
- `marker.png` — the figure to scan (print it, or open it on a second screen)
- `heart.glb` — the 3D model (CC BY 4.0, dcpisith; see ../vr/models/ATTRIBUTION.txt)
- `targets.mind` — **you must generate this once** (see below)

## One-time step: make `targets.mind` (~30 seconds)
MindAR tracks a *compiled* version of the image, not the PNG directly.
1. Open the MindAR image compiler: https://hiukim.github.io/mind-ar-js-doc/tools/compile
2. Drag in `marker.png`, click **Start**, then **Download** — you get `targets.mind`.
3. Put `targets.mind` in this folder (next to `index.html`).

## Run it (must be https or localhost — the camera needs a secure context)
```bash
npx serve        # then open the printed/second-screen marker and scan it
```
Open the localhost URL on your computer, or host on GitHub Pages (https) and
open on your phone. Allow camera access when prompted.

## Hosting on GitHub Pages
Same as the VR module: push this folder to a repo, then Settings → Pages →
Deploy from a branch → main → /(root). The site is served over https, which
the camera requires. Generate a QR code from the Pages URL for the report.

## Tuning (if needed)
- If the heart sits too large/small or floats off the page, adjust `scale` and
  the `position` z-value on the `#arHeartModel` entity in `index.html`.
- If it appears lying flat, add an x-rotation (e.g. `rotation="-90 0 0"`).
