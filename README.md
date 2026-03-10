# 360° Viewer + Playlist Builder

> **Work in progress** — prototype, expect rough edges.

A self-contained, zero-dependency pair of HTML tools for sharing 360° equirectangular panoramas with clients. No backend required.

---

## Files

| File | Purpose |
|---|---|
| `360builder.html` | Compose a playlist, export as JSON or a shareable URL |
| `360viewer.html` | WebGL viewer that loads and displays the panoramas |
| `playlist.json` | Example playlist file |

---

## Live viewer

**`https://nuninhosousa25.github.io/360-view/`**

---

## How it works

1. Open **`360builder.html`** and add panorama images (paste URLs or upload local files).
2. Label and reorder images by dragging cards.
3. **Download JSON** — download the playlist file.
4. Host the JSON somewhere (GitHub, your server, etc.).
5. Use the **Share Link Generator** in the builder to produce the final viewer URL, or construct it manually: `https://nuninhosousa25.github.io/360-view/?playlist=<your-json-url>`

---

## Viewer URL parameters

| Param | Description |
|---|---|
| `?url=` | Single panorama image URL |
| `?urls=url1,url2` | Comma-separated list of URLs |
| `?playlist=` | URL to a hosted `.json` playlist file |

---

## Playlist JSON format

```json
{
  "title": "Client Tour — Building A",
  "created": "2026-01-01T00:00:00.000Z",
  "images": [
    { "url": "https://yourserver.com/photo1.jpg", "label": "Entrance" },
    { "url": "https://yourserver.com/photo2.jpg", "label": "Living Room" }
  ]
}
```

---

## Controls (viewer)

| Input | Action |
|---|---|
| Click + drag | Look around |
| Scroll wheel | Zoom in / out |
| Pinch (touch) | Zoom in / out |
| Arrow keys | Pan |
| `+` / `-` | Zoom |
| `f` | Toggle fullscreen |
| `Shift + →/←` | Next / previous image |

---

## Dependencies

- [Three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js) — loaded via CDN in the viewer
- Google Fonts (Bebas Neue, DM Sans) — loaded via CDN

No build step. No npm. Just open the HTML files in a browser.

---

## Notes & limitations

- Local files uploaded in the builder are embedded as **base64** inside the JSON — fine for local preview only. For client sharing, upload images to a server and use URLs instead.
- Images must support **CORS** for the Three.js texture loader to work when hosted remotely.
