# French 180 Pro 3.0.1 — GitHub Pages Edition

A static GitHub Pages build of French 180 Pro. This edition moves the learning interface out of the Google Apps Script iframe so browser microphone permissions can work normally on HTTPS.

## What changed from Apps Script V3.0

- The app is a normal static HTTPS site instead of an Apps Script iframe.
- Speech practice now requests microphone permission directly through the browser.
- Settings includes microphone diagnostics and plain-language permission errors.
- Apps Script cloud sync was removed from the frontend; progress is saved locally and can be exported/imported as JSON.
- A service worker and web-app manifest make the app installable/offline-capable after the first load.
- The existing `french180pro_v2` local-storage key is preserved, so the same-browser data format remains compatible.

## Publish on GitHub Pages

1. Create a GitHub repository, for example `french-180-pro`.
2. Upload **all files in this package**, including the `.github` folder.
3. Make sure the default branch is `main`.
4. In **Settings → Pages**, set **Source** to **GitHub Actions** if GitHub does not select it automatically.
5. Open the **Actions** tab and let `Deploy French 180 Pro to GitHub Pages` finish.
6. In **Settings → Pages**, use **Visit site** to open the HTTPS `github.io` address.
7. In the app, open **Settings → Microphone & backup → Enable microphone** and choose **Allow**.

GitHub Pages must be opened through its HTTPS URL for microphone access. Do not test microphone permissions by double-clicking `index.html` as a local `file://` page.

## Browser recommendation

For the current Web Speech recognition API, current Chrome or Edge is recommended. Text-to-speech and the rest of the course can still work when speech recognition is unavailable.

## Move your V3.0 progress

If you are switching from the Apps Script deployment on the same computer/browser, the two origins have different browser storage, so data does **not** automatically cross from `script.google.com` to `github.io`.

1. In the Apps Script version, export your progress JSON.
2. Open the GitHub Pages version.
3. Go to **Settings → Microphone & backup**.
4. Choose the exported `.json` file under **Export backup / Import**.

After import, your course day, cards, SRS, mistakes, journals, adaptive profile, and compatible settings are migrated by the existing V3 migration code.

## Updating the app

Edit/push files to `main`. The included GitHub Actions workflow automatically redeploys the static site.

## Privacy

The app itself has no analytics or advertising code. Study progress is stored in browser local storage. Exported backups are files you control. Browser speech recognition behavior is controlled by the browser/vendor; in some browsers, recognition may use an online speech service.
