# Internly PWA

A zero-budget, local-first PWA conversion of the supplied Internly HTML app.

## Included
- Original four-tab internship log/report workflow and styling.
- IndexedDB local persistence, with localStorage fallback.
- Offline app shell via service worker.
- JSON export/import backup.
- Gemini API report generation using a user-supplied key.

## Important AI/privacy notes
- The original Claude artifact runtime is not available outside Claude artifacts; this build replaces it with the Gemini Developer API.
- Create a Gemini API key at https://aistudio.google.com/app/apikey and add it in **Internship details → AI report generation**.
- The key is stored in this browser's local storage and is not included in JSON backups. Anyone with access to this browser profile may be able to inspect browser storage; do not use a shared device.
- When generating a report, Internly sends the report prompt (internship details and daily log text) to Google. Google's current Gemini API pricing page describes free-tier submitted content as being used to improve Google products. Do not submit confidential employer/client information.
- Free-tier model access and rate limits can change. This project does not guarantee unlimited free AI usage.
- AI generation requires internet. Logging, browsing saved entries, and report viewing work offline once the app has been loaded/cached.

## Test locally
A PWA service worker requires HTTPS or localhost. Do not open `index.html` directly using `file://`.

If Python 3 is installed:
```bash
python -m http.server 8000
```
Then open http://localhost:8000 in Chrome.

## Free hosting (GitHub Pages)
1. Create a GitHub account if you do not have one.
2. Create a new public repository, for example `internly-pwa`.
3. Upload the **contents** of this folder (not the folder itself) to the repository root.
4. In the repository, open **Settings → Pages**.
5. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish the site. Your URL will look like `https://YOUR-USERNAME.github.io/internly-pwa/`.
7. Open that HTTPS URL in Chrome on Android, use the browser menu, and choose **Install app** or **Add to Home screen**.

GitHub Pages is static hosting; there is no server-side database. Your data remains in the browser storage on each device and does not sync across devices.

## Android installation
Open the hosted HTTPS URL in Chrome on Android → browser menu → **Install app** (or **Add to Home screen**). The PWA does not need Play Store publication.

## Backups
Use **Internship details → Your data & backups → Export backup** periodically. Store the JSON file somewhere safe. Importing a backup replaces the current on-device Internly data.
