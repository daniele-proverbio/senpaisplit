# SenpaiSplit 🦅

A progressive web app (PWA) for splitting restaurant bills proportionally by seniority weight. Works fully offline once installed.

---

## Deploy to GitHub Pages (5 minutes)

### Step 1 — Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in (or create a free account)
2. Click **+** → **New repository**
3. Name it `senpaisplit` (or anything you like)
4. Set it to **Public**
5. Click **Create repository**

### Step 2 — Upload the files

1. On your new repo page, click **uploading an existing file**
2. Drag and drop **all** of these files into the upload area:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
   - `.nojekyll`
3. Scroll down, click **Commit changes**

### Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under **Source**, select **Deploy from a branch**
3. Choose branch: `main`, folder: `/ (root)`
4. Click **Save**

After ~60 seconds your app will be live at:
```
https://YOUR-USERNAME.github.io/senpaisplit/
```

---

## Install as an app (PWA)

Once live on HTTPS, visitors can install SenpaiSplit as a native-like app:

| Platform | How to install |
|----------|---------------|
| **iPhone / iPad** | Open in Safari → Share → **Add to Home Screen** |
| **Android** | Open in Chrome → three-dot menu → **Add to Home Screen** / **Install app** |
| **Desktop Chrome / Edge** | Click the install icon (⊕) in the address bar |

The app works fully **offline** after the first visit — no internet needed at the restaurant.

---

## How to share the link

Send users directly to:
```
https://YOUR-USERNAME.github.io/senpaisplit/
```

They can open it in any browser and install it from there. No app store required.

---

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire app — UI, logic, i18n (EN/JA), groups, algorithm |
| `manifest.json` | PWA metadata: name, icons, display mode |
| `sw.js` | Service worker: offline caching |
| `icon-192.png` | App icon (192×192) |
| `icon-512.png` | App icon (512×512) |
| `.nojekyll` | Tells GitHub Pages not to run Jekyll (required) |

---

## Algorithm

The bill is split proportionally among non-fixed people:

1. **Weight** (1–5): base seniority weight per person
2. **Drink status**: `no drink` → −0.5 · `drink` → ±0 · `drink more` → +0.5
3. **Fixed sum** (weight ≥ 4): person pays exactly this amount; remainder is split among everyone else
4. **Rounding**: all shares except the heaviest are floored/rounded; the heaviest absorbs the remainder — guaranteeing the total always matches exactly

---

## Credits

App developed and provided by Riccardo Muolo and Daniele Proverbio.
