[README.md](https://github.com/user-attachments/files/31867830/README.md)

# Attendance PWA — setup

This is a real installable app: home-screen icon, works fully offline, no Claude account needed. Data is stored only on your phone (localStorage), nothing leaves the device.

One catch: to install to your home screen with offline support working properly, Chrome needs to load it over **https://** or **localhost** at least once — not directly from a `file://` path. After that first load it's cached and works with airplane mode on.

## Option A — GitHub Pages (recommended, permanent, free)

1. Create a new GitHub repo (public), e.g. `attendance-app`.
2. Upload these 5 files to the repo root: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `icon-512-maskable.png`.
3. In the repo: Settings → Pages → Source: `main` branch, `/ (root)` → Save.
4. Wait ~1 minute, then open the given `https://<username>.github.io/attendance-app/` URL in Chrome on your phone.
5. Chrome menu (⋮) → **Add to Home screen**.
6. Done — tap the icon anytime, including offline.

## Option B — quick local test tonight (via Termux)

Good for testing right now without setting up GitHub.

```
pkg install python -y
```

```
cd /path/to/attendance-pwa && python -m http.server 8080
```

Then, on the same phone, open Chrome to:

```
http://localhost:8080
```

Add to home screen from there. Note: this only works while the Termux server is running in that session — for a permanent icon that works anytime, use Option A instead.

## Updating later

If you want new features added, just edit `index.html` and re-upload/re-serve — the service worker will pick up changes on next launch (you may need to close and reopen the app once for the update to take effect).
