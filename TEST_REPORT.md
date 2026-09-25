# French 180 Pro 3.0.1 — GitHub Pages Test Report

## Static validation

- `index.html` client JavaScript passes `node --check` syntax validation.
- `sw.js` passes `node --check` syntax validation.
- 158 HTML element IDs are unique; no duplicate IDs were found.
- Two JavaScript IDs (`cefrInput` and `cefrSpeechFeedback`) are intentionally created dynamically by the CEFR assessment renderer.
- No Google Apps Script frontend calls (`google.script.run`, `HtmlService`, `PropertiesService`) remain in the static app.
- Web app manifest parses successfully and uses relative `./` start/scope paths suitable for a GitHub project Pages subdirectory.
- Service-worker core assets all exist.
- GitHub Pages workflow YAML parses successfully.

## Microphone architecture

- Speech practice uses `navigator.mediaDevices.getUserMedia({audio:true})` to request microphone permission from the top-level HTTPS page.
- Speech recognition uses `window.SpeechRecognition || window.webkitSpeechRecognition` when available.
- The UI checks secure-context status and reports blocked/denied/not-found/busy microphone states in plain language.
- A browser without Web Speech recognition can still use all non-microphone course features and text-to-speech.

## Deployment configuration

The included workflow follows GitHub's static Pages deployment pattern:

- `actions/checkout@v6`
- `actions/configure-pages@v5`
- `actions/upload-pages-artifact@v4`
- `actions/deploy-pages@v4`
- `pages: write` and `id-token: write` permissions
- `github-pages` deployment environment

## Data migration

Browser storage does not cross origins. Progress from the Apps Script edition must be exported as JSON there and imported into the GitHub Pages edition. The V3-compatible state migration code is retained.

## Runtime testing note

This execution environment blocks automated Chromium navigation to locally served/file URLs, so a full browser-permission prompt could not be exercised here. Static syntax, dependency, asset, manifest, workflow, and microphone-path checks passed. Final microphone permission must be verified on the live HTTPS GitHub Pages URL in the user's browser.
