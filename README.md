[README.md](https://github.com/user-attachments/files/32125125/README.md)
# Rider Log

A self-contained web app / installable PWA for filling out, saving, and compiling monthly student transportation rider logs — no server, no accounts, no backend required.

**Live demo:** _add your GitHub Pages URL here once deployed, e.g. `https://yourusername.github.io/rider-log-pwa/`_

---

## What it does

- Fill out a digital version of the paper Rider Log form (student, pickup address, districts, mileage totals, and a full 31-day AM/PM grid).
- Save multiple monthly logs — they persist in the browser between visits.
- Draw a signature once; it's automatically stamped onto every log when compiled.
- Select any combination of saved logs and compile them into a single multi-page PDF.
- Share that PDF via your device's native share sheet (Mail, Gmail, etc.) or download it directly.
- Export all saved logs + signature to a single backup file, and import that file back in — handy for moving data between devices or keeping a backup.
- Installable as an app on desktop, Android, and iPhone (Add to Home Screen) via PWA support, and works offline after the first load.

## Getting started

No build step, no dependencies to install. This is a static site.

1. Clone or download this repository.
2. Open `index.html` directly in a browser, **or** serve the folder with any static file server, **or** deploy it with GitHub Pages (see below).

### Deploying with GitHub Pages

1. Push all files in this repo to GitHub, keeping the filenames exactly as they are (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch," choose `main` and `/ (root)`, then save.
4. After a minute or two, GitHub gives you a live URL like `https://yourusername.github.io/repo-name/`. Share that link — anyone who opens it can use the app immediately, no download or install required.

### Installing as an app (optional)

Once it's hosted somewhere (GitHub Pages or otherwise):

- **iPhone/iPad (Safari):** open the link → Share button → "Add to Home Screen."
- **Android/Chrome/Edge:** open the link → browser menu → "Install app" (or the install icon in the address bar).

It then opens full-screen with its own icon, and works offline after the first visit.

## File structure

```
├── index.html       # the entire app — UI, logic, PDF generation
├── manifest.json     # PWA manifest (name, icons, colors, display mode)
├── sw.js             # service worker — enables offline use once installed
├── icon-192.png       # app icon (small)
└── icon-512.png       # app icon (large)
```

Everything runs client-side. `index.html` pulls in two external libraries at runtime from a CDN (jsPDF and jsPDF-AutoTable, for building the compiled PDF) — an internet connection is needed the first time these load, after which the service worker caches them for offline use.

## Data storage & privacy

- All data (saved logs and the signature) is stored **locally in the browser**, using IndexedDB (or Claude's built-in storage, when running inside a Claude.ai artifact).
- Nothing is sent to a server. There is no backend, no database, and no account system.
- Because storage is per-browser and per-device, data does **not** sync automatically between devices or between different people opening the same link — each visitor gets their own private local copy.
- Use **Export All Data** / **Import Data** (in the app) to manually move data between devices or keep a backup.
- If your organization plans to store real student information long-term, confirm with your school district's IT/compliance office whether FERPA or other student-privacy rules apply — this app does not currently include the access controls, audit logging, or centralized storage that a compliance-managed system would need.

## Known limitations

- No multi-user accounts or centralized admin view — this is a personal/per-driver tool, not a fleet management system.
- No live GPS/mapping features.
- Data does not sync across devices without manual export/import.
- Browser extension distribution isn't supported on iOS; this project intentionally uses the PWA approach instead so it works across all platforms from one codebase.

## Roadmap ideas

- Real backend + accounts for centralized, synced data across drivers and devices.
- Assigning students to drivers with attached student records.
- GPS-assisted address entry / route mapping.

## License

_Add a license of your choice here (e.g. MIT) if you plan to share this publicly._
