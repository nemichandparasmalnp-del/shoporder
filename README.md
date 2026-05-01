# ShopOrder 🛍️

A mobile-first **Retail Order Management PWA** — works on phone, tablet, and desktop. Install it like a native app directly from the browser.

---

## Features

- 📦 Order taking with product catalog
- 📊 Live dashboard with status filters
- 📅 Date-based order navigation with incomplete-delivery alerts
- 🗂️ Tally XML / CSV catalog import
- 📲 Installable as a PWA (Android, iOS, Windows, Mac)
- ⚡ Offline-capable via Service Worker

---

## Deploy in 2 Minutes (Netlify)

1. Go to [netlify.com](https://netlify.com) and sign up for free
2. Click **"Add new site" → "Deploy manually"**
3. Drag and drop this entire folder onto the Netlify drop zone
4. You'll get a live URL like `https://shoporder-xyz.netlify.app`

That's it — open the URL on any device and install it as an app.

---

## Deploy via GitHub + Netlify (Recommended for updates)

1. Push this repo to GitHub
2. Go to Netlify → **"Add new site" → "Import an existing project"**
3. Connect your GitHub repo
4. Build settings: leave blank (static site, no build command needed)
5. Click **Deploy**

Every time you push to `main`, Netlify auto-deploys.

---

## Install as an App

| Device | Steps |
|---|---|
| **Android** | Chrome → 3-dot menu → "Add to Home Screen" |
| **iPhone / iPad** | Safari → Share icon → "Add to Home Screen" |
| **Windows / Mac** | Chrome → install icon in address bar |

---

## Real-Time Sync (Optional)

By default, orders are stored locally in each browser session. To sync across devices in real time, integrate **Firebase Firestore**:

1. Create a free project at [firebase.google.com](https://firebase.google.com)
2. Enable Firestore Database
3. Replace the in-memory `orders` array in `index.html` with Firestore read/write calls

---

## File Structure

```
shoporder/
├── index.html       ← Main app (single file)
├── manifest.json    ← PWA manifest
├── sw.js            ← Service worker (offline support)
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── .gitignore
```

---

## Tally Catalog Import

**Tally → Display → Stock Summary → `Alt+E` → Export as XML or CSV**

Only the Name / Item / Particulars column is needed. Price is ignored.
