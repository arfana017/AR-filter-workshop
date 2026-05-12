# 👻 GWC × Snapchat — AR Filter Workshop

Welcome! Today we're building a **live AR filter** that runs in your browser using your webcam — no apps, no installs.

---

**Open `https://arfana017.github.io/ar-filter-workshop`**
2. When your browser asks **"allow camera access?"** — click **Allow**
3. Wait about 5–10 seconds for the face detection model to load
4. You should see yourself on screen with filter controls on the right!

## 🎛️ What's on screen

| Thing | What it does |
|---|---|
| Filter buttons | Switch between warmth, grayscale, dog ears, sunglasses, etc. |
| Intensity slider | Make the filter stronger or subtler |
| Text overlay box | Type anything — it appears on your video like a Snap caption |
| Text size slider | Make the caption bigger or smaller |
| Colour swatches | Change the caption colour |
| Show landmarks toggle | Reveals the 68 face-tracking dots the neural net uses 🤯 |

---

## 🧑‍💻 What we'll code together

1. **A pixel filter** — loop through every pixel and change its RGB values (this is how warmth, grayscale, and beauty filters work)
2. **A face overlay** — use landmark coordinates to place the dog ears / sunglasses exactly on your face
3. **A text layer** — render a Snapchat-style caption with outline + fill


---

## ❓ Troubleshooting

**Stuck on "loading face detection models..."**
→ Check your internet connection. The model files (~270KB) need to download once. Refresh and try again.

**Black screen / no camera**
→ Make sure you clicked "Allow" when the browser asked for camera access. If you missed it, click the 🔒 or 📷 icon in your browser's address bar and allow camera.

**Filters not aligning with my face**
→ Make sure your face is reasonably well-lit and centred. The detector works best when your whole face is visible.

**Camera works but face isn't being detected**
→ Toggle on "show landmarks" — if dots appear, detection is working fine. Try moving further from or closer to the camera.

---

## 🔗 Want to go further after today?

- **[Snap Lens Studio](https://ar.snap.com/lens-studio)** — the actual tool Snapchat engineers use. Free, and you can publish filters to Snapchat.
- **[face-api.js docs](https://github.com/justadudewhohacks/face-api.js)** — the library we used
- **[MDN Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)** — everything you can do with the `<canvas>` element
- **[68 landmark point map](https://www.researchgate.net/figure/The-ibug-68-facial-landmark-points-mark-up_fig9_327500528)** — which numbered point maps to which part of the face

See you next week when our Snapchat engineer guest comes in! 🎉
