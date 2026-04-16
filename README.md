# SenpaiSplit 🦅

A progressive web app (PWA) for splitting restaurant bills proportionally by seniority weight. Works fully offline once installed.

---

## Install as an app (PWA)

Once live on HTTPS, visitors can install SenpaiSplit as a native-like app, after visiting its website page:

| Platform | How to install |
|----------|---------------|
| **iPhone / iPad** | Open in Safari → Share → **Add to Home Screen** |
| **Android** | Open in Chrome → three-dot menu → **Add to Home Screen** / **Install app** |
| **Desktop Chrome / Edge** | Click the install icon (⊕) in the address bar |

The app works fully **offline** after the first visit — no internet needed at the restaurant.

---

## How to share the link

Users can directly access:
```
https://daniele-proverbio.github.io/senpaisplit/[https://daniele-proverbio.github.io/senpaisplit/]
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
2. **Drink status**: `no drink` → −0.5 · `drink` → 0 · `drink more` → +0.5
3. **Fixed sum** (weight ≥ 4): a person can pay exact amounts; the remainder is split among everyone else
4. **Rounding**: all shares except the heaviest are floored/rounded; the heaviest absorbs the remainder — guaranteeing the total always matches exactly
5. **Saving groups**: groups can be saved for future events

---

## Credits

App developed and provided by Riccardo Muolo and Daniele Proverbio.
