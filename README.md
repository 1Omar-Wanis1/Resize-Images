# Enlarger

**Bulk resize, upscale, enhance and convert hundreds of photos at once — entirely in your browser.**

No upload. No account. No server. No file-size limit. Your images never leave your machine, because there is nowhere for them to go.

> 🔗 **Live:** https://YOUR-USERNAME.github.io/YOUR-REPO/
> *(replace this line with your real link)*

---

## Why it exists

Most bulk image resizers either make you upload private photos to somebody else's server, cap you at 10–20 files, charge a subscription, or need a desktop install. Enlarger is a single HTML file that does the whole job locally, using your own CPU cores — and it's free.

---

## What it does

### Resize — four ways
| Mode | Use it when |
|---|---|
| **In Pixels** | You need an exact pixel size |
| **In Percentage** | Scale every image by the same factor, whatever its original size |
| **In Print Size** | You're printing — work in inches/cm/mm at a chosen DPI |
| **Based on one side** | Fix the long side, short side, width or height; the rest follows |

Plus preserve-aspect-ratio, smart-cropping (exact size, trims edges), smart-filling (exact size, pads with a colour), long-side matching for mixed portrait/landscape batches, and a don't-upscale-small-images guard.

Five resampling filters: **Nearest**, **Bilinear**, **Bicubic**, **Lanczos3** (sharpest) and **Canvas Smooth** (GPU, fastest — used automatically for very large outputs).

### Enhance pixelated photos
Denoise runs on the *source* before enlarging — which is where pixelation and JPEG blocking actually live — then Lanczos upscaling, then edge-aware sharpening that lifts real detail without amplifying grain.

Measured against a clean reference image, **Enhance Medium scored +2.9 dB PSNR over a plain resize** of the same degraded source. For contrast, ordinary sharpening scored *worse* than doing nothing on a noisy image — which is exactly why this pipeline exists.

> This is classical image processing, not AI super-resolution. It will not invent detail that was never captured — but heavily compressed and pixelated sources come out markedly cleaner.

### Control the file weight
Set **"keep every file under 2 MB"** (or any KB/MB figure) and Enlarger binary-searches the encoder quality to find the best result that still fits. If quality alone can't get there, it can progressively shrink dimensions until it does. Ideal for upload limits and page-speed budgets.

### Convert formats
JPEG · PNG · WebP · AVIF · or keep each file's original format.
Reads JPG, PNG, WebP, AVIF, GIF, BMP, SVG and ICO.

### Preview before you commit
Drag-to-compare slider between the original and the result, zoom to 400%, arrow through the batch — and it reports the **real encoded output size**, so you can confirm a size limit is met before processing 500 files. Huge outputs render as a true 100% centre crop so preview stays fast.

### Work on a subset
Tick individual images, then apply the current settings to **just those** — they keep their own configuration while you set something different for everyone else. One batch, two treatments. You can also preview, convert or remove only the selection.

### Everything else
- Up to **500 images comfortably**, hard cap 2000
- Save straight into a folder on your disk, or download as a ZIP (auto-splitting for large batches)
- Bulk rename with patterns (`{name}`, `###`, `{w}x{h}`, `{date}`…) or rename any single file by clicking it
- UPPERCASE extensions · keep original date/time · ask before overwrite · error reporting
- Writes real **DPI metadata** into JPEG (JFIF) and PNG (pHYs) so print labs open your file at the correct physical size instead of assuming 72 DPI
- Multi-core processing via Web Workers, with worker count auto-tuned to your output size
- Live progress: per-file status, size before/after, compression ratio, elapsed time and ETA
- Dark and light themes, a guided 11-step tour, and an ⓘ explanation on every single option

---

## How to use it

1. **Drop** your images (or a whole folder) onto the page.
2. **Set the size** in step 02 — this is the only required step.
3. *(Optional)* Turn on Enhance, set a file-weight limit, choose a format, set up renaming.
4. **Choose where they go** — a folder on your PC, or a ZIP download.
5. **Preview** one image to check it looks right.
6. Hit **Convert**.

If you haven't changed a single setting, Enlarger stops and tells you rather than wasting your time on a no-op. Changing any one option is enough to proceed.

---

## Browser support

| Feature | Chrome / Edge / Opera | Firefox | Safari |
|---|---|---|---|
| Resize, enhance, convert | ✅ | ✅ | ✅ |
| Multi-core processing | ✅ | ✅ | ✅ |
| **Save into a folder** | ✅ | ❌ | ❌ |
| ZIP download | ✅ | ✅ | ✅ |
| AVIF output | ✅ | ✅ | ⚠️ varies |

Saving directly into a folder needs the File System Access API, which currently only Chromium browsers implement. Everywhere else, Enlarger falls back to ZIP automatically and tells you so.

**For very large batches** (hundreds of print-size images), choose the folder destination rather than ZIP — a ZIP has to be assembled in memory, whereas folder output writes each file to disk as it finishes.

---

## Privacy

Everything runs client-side via the Canvas API, Web Workers and the File System Access API.

- No image or filename is ever transmitted anywhere
- No server, no database, no accounts
- No analytics, cookies or tracking
- Works offline once the page has loaded

You can verify all of this yourself: open your browser's Network tab and watch it stay silent while you process a batch.

---

## Running it locally

It's one file with no build step.

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
cd YOUR-REPO
```

Then open `index.html` in your browser. That's it.

> Note: folder-saving and Web Workers need a real origin. If you open the file directly via `file://` and something misbehaves, serve it over HTTP instead:
> ```bash
> python -m http.server 8000
> ```
> then visit `http://localhost:8000`.

---

## Built with

Vanilla HTML, CSS and JavaScript — no framework, no build tooling.

- [JSZip](https://stuk.github.io/jszip/) for archive creation *(MIT/GPLv3)*
- Poppins, IBM Plex Mono and Archivo Black typefaces *(SIL Open Font License 1.1)*

---

## License

**Copyright © 2026 Omar Wanis. All rights reserved.**

Enlarger is **free to use** — process as many of your own images as you like, for anything, including commercial work.

However, the source code is *not* open source. You may **not** copy, modify, fork, redistribute or re-host it, and you may not remove the author credit. The code is public so the page can be served and so anyone can verify the privacy claims above — that is not the same as placing it in the public domain.

See [LICENSE](LICENSE) for the full terms, including the third-party components which remain under their own licenses.

For permission to do anything the license doesn't allow, please get in touch.

---

## Author

**Designed & built by Omar Wanis**
