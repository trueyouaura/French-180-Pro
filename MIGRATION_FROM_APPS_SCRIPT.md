# Migrating from the Apps Script edition

## Before you switch

Open the old French 180 Pro V3 Apps Script app and export a JSON backup from Settings.

## Import into GitHub Pages

Open the live GitHub Pages site, then:

1. Settings
2. Microphone & backup
3. Select the exported JSON file
4. Confirm the app returns to your existing course progress

## Microphone setup

1. Open the live `https://<username>.github.io/<repository>/` site.
2. Go to Settings → Microphone & backup.
3. Select **Enable microphone**.
4. Choose **Allow** in the browser prompt.
5. If blocked, open the browser's site controls/lock icon, change Microphone to Allow, and reload.

If the app reports that speech recognition is unavailable even after microphone permission is allowed, use a current version of Chrome or Edge. This is separate from microphone permission: a browser can allow the microphone but not implement the Web Speech recognition API.
