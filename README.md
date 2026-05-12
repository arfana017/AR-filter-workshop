# 👻 GWC × Snapchat — AR Filter Workshop

A live, in-browser AR filter builder using your **real webcam**, face landmark detection, and the Canvas API. No installs — runs in any modern browser.

Built for Girls Who Code × Snapchat guest speaker prep.

---

## 🚀 Quick setup (do this tonight before the meeting)

### 1. Download the face-api.js models

The face detection models are neural network weight files that need to be in a `/models` folder. Run this in your terminal from the project root:

```bash
mkdir models

# Tiny face detector (fast, good for real-time)
curl -L -o models/tiny_face_detector_model-weights_manifest.json \
  https://raw.githubusercontent.com/justadudewhohacks/face-api.js/master/weights/tiny_face_detector_model-weights_manifest.json
curl -L -o models/tiny_face_detector_model-shard1 \
  https://raw.githubusercontent.com/justadudewhohacks/face-api.js/master/weights/tiny_face_detector_model-shard1

# 68-point landmark model (tiny version)
curl -L -o models/face_landmark_68_tiny_model-weights_manifest.json \
  https://raw.githubusercontent.com/justadudewhohacks/face-api.js/master/weights/face_landmark_68_tiny_model-weights_manifest.json
curl -L -o models/face_landmark_68_tiny_model-shard1 \
  https://raw.githubusercontent.com/justadudewhohacks/face-api.js/master/weights/face_landmark_68_tiny_model-shard1
```

Or just download the `/weights` folder directly from the [face-api.js repo](https://github.com/justadudewhohacks/face-api.js/tree/master/weights) and rename it to `models`.

---

### 2. Add your overlay images

Drop **PNG files with transparent backgrounds** into the `/assets` folder:

| Filename | What it is |
|---|---|
| `assets/dog-ears.png` | Dog ears + nose overlay |
| `assets/sunglasses.png` | Sunglasses overlay |
| `assets/crown.png` | Crown overlay |

**Where to get free PNGs:**
- Search "[item] PNG transparent background" on Google Images
- [PNGWing](https://www.pngwing.com) — huge library, free for non-commercial
- [FreePNG](https://www.freepng.es)
- Or draw your own in Figma and export as PNG with transparent bg!

---

### 3. Run it locally (important — webcam needs a server)

Browsers block webcam access on `file://` URLs for security. You need a local server:

```bash
# If you have Python installed (most Macs/Linux):
python3 -m http.server 8080
# Then open: http://localhost:8080

# If you have Node.js:
npx serve .
# Then open the URL it gives you
```

Or use the **VS Code Live Server extension** — right-click `index.html` → Open with Live Server.

---

### 4. Host on GitHub Pages (so everyone can open it on their own laptop)

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Everyone opens `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME`
5. Browser will ask for camera permission — click Allow

---

## 📁 File structure

```
ar-filter-workshop/
├── index.html          ← all the code lives here
├── README.md           ← you're reading this
├── models/             ← face-api neural net weights (you download these)
│   ├── tiny_face_detector_model-weights_manifest.json
│   ├── tiny_face_detector_model-shard1
│   ├── face_landmark_68_tiny_model-weights_manifest.json
│   └── face_landmark_68_tiny_model-shard1
└── assets/             ← your PNG overlays go here
    ├── dog-ears.png
    ├── sunglasses.png
    └── crown.png
```

---

## 🧑‍💻 Workshop flow (for the facilitator)

### Pre-built for you (plumbing — just explain, don't code live)
- Webcam → `<video>` → `<canvas>` pipe
- `requestAnimationFrame` render loop
- face-api detection running in parallel

### Code together (the fun part)
1. **`applyPixelFilter()`** — warmth filter, pixel-by-pixel RGB manipulation (~8 min)
2. **`drawEars()` / `drawSunglasses()`** — placing overlays using landmark coordinates (~8 min)
3. **`drawText()`** — canvas text with stroke + fill (~5 min)

### Free build (last 10 min)
- Combine two filters
- Invent a new pixel effect
- Try swapping which landmark points the overlay anchors to

---

## 🤝 The Snapchat connection (bridge moment)

After coding `drawEars()`, say:

> "We just used 68 2D landmark points to guess where to put the ears. Snapchat's production pipeline uses **hundreds of 3D landmarks**, tracked by a convolutional neural network running on the phone's GPU at 60fps. The model knows depth — so when you tilt your head, the ears tilt too. That's what your guest engineer ships. We built the idea; they built it at scale."

---

## 🔗 Resources for the club

- [face-api.js docs](https://github.com/justadudewhohacks/face-api.js)
- [MDN Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
- [Snap Lens Studio](https://ar.snap.com/lens-studio) — the real tool
- [68 landmark point map](https://ibug.doc.ic.ac.uk/resources/facial-point-annotations/)
- [MDN getUserMedia](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)
