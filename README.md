# MOTION — Keep Life Moving.

Everyday-life convenience and logistics prototype. Mobile-first PWA, wrapped for native iOS/Android via Capacitor.

## 1. Deploy as a website + installable PWA (GitHub Pages)

This repo already includes `.github/workflows/deploy.yml`, which auto-deploys on every push to `main`.

Setup (one time):
1. Push this folder to a new GitHub repo.
2. In the repo: **Settings → Pages → Source → GitHub Actions**.
3. Push to `main` (or re-run the workflow from the **Actions** tab).
4. Your app will be live at `https://<your-username>.github.io/<repo-name>/`.

Open that URL on a phone:
- **Android/Chrome** — you'll get an "Install app" prompt (or Menu → Install app).
- **iPhone/Safari** — Share → Add to Home Screen.

No build step needed — it's static HTML/CSS/JS.

## 2. Build as a real native app (iOS / Android via Capacitor)

This folder is pre-configured for [Capacitor](https://capacitorjs.com), which wraps the web app in a native shell so it can go through TestFlight / the App Store / Google Play.

This step needs a real machine with Xcode (for iOS) and/or Android Studio (for Android) — it can't be built inside this chat. The recommended path is **Claude Code**, running locally, which can run these commands and fix build errors as they come up.

```bash
npm install
npx cap add ios       # requires macOS + Xcode
npx cap add android    # requires Android Studio
npx cap sync
npx cap open ios       # opens Xcode
npx cap open android   # opens Android Studio
```

From there, Xcode/Android Studio handles code signing, icons/splash screens, and submission to TestFlight or the Play Console.

## Notes

- `index.html` is the entire app (vanilla JS, no build step) — this is also `webDir` for Capacitor.
- `manifest.json` / `sw.js` power the installable-PWA behavior; they're not needed once wrapped natively but don't hurt.
- All data (orders, pricing, the "AI" request parser) is mocked in-memory — see the `IMPORTANT PRODUCT PRINCIPLE` section of the original brief for the intended real-backend replacement plan.
