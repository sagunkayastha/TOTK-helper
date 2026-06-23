# TotK Trackers

Offline, browser-based trackers for *The Legend of Zelda: Tears of the Kingdom*. Reads your save file locally (in the browser, nothing uploaded) and shows your progress.

## Contents
- `index.html` — hub / launcher
- `map/` — full collectibles map: shrines, lightroots, koroks, caves, bubbuls, bosses and more, across Surface / Sky / Depths layers
- `armor/` — all 135 armor pieces with set bonus, defense, location, wiki link
- `recipes/` — cooking reference by effect, with a "how to cook" guide

## How to run

No build step, no install — it's plain HTML/JS.

**Easiest:** double-click `index.html` so it opens in **Chrome or Edge** (the save-reading uses the File System Access API, which Firefox/Safari don't support).

**If folder-picking is blocked** (some setups don't allow it from `file://`), serve the folder over localhost from a terminal in this directory:

```
python3 -m http.server 8000      # then open http://localhost:8000
```
(or `npx serve` if you have Node.)

**Then:** on the Map or Armor page click **Refresh** and pick the folder that holds `slot_00 … slot_05`. It auto-loads your most-progressed slot and remembers the folder for next time.

### About your save
The app only ever **reads** the save — it never writes to it. To be extra safe, copy your `slot_00 … slot_05` folder somewhere else first and point the tracker at the copy, or use the **Back up saves** button on the Map / Armor pages to copy them to a folder you choose. The Recipes page needs no save and works in any browser.

## Install it as an app on iPhone / iPad (PWA)

This is a Progressive Web App — it installs to your home screen with an icon, runs fullscreen, and works offline after the first load. No App Store, no Xcode, no cable.

**1. Host it on GitHub Pages** (free, and gives the `https` that iOS requires):
1. Create a GitHub repo and upload everything in this folder (keep the folder structure: `index.html`, `manifest.webmanifest`, `sw.js`, the icons, and the `map/ armor/ recipes/` folders).
2. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**, pick `main` / `/root`, **Save**.
3. After a minute it's live at `https://<your-username>.github.io/<repo-name>/`.

**2. Add it to your home screen:** open that URL in **Safari** on the iPad/iPhone → **Share** → **Add to Home Screen**. You'll get the gem icon and a fullscreen app.

### Loading your save on iOS
iPad/iPhone Safari can't auto-scan a save folder, so it uses a one-file upload instead:
1. On your PC, copy your `progress.sav` into **OneDrive** or **Google Drive** (whichever you sync).
2. In the app, open **Map** or **Armor** and tap **Refresh** → the iOS file picker opens → browse to **OneDrive / Google Drive / Files** and pick `progress.sav`.

It loads instantly and re-reading later is just: re-sync the file, tap Refresh, pick it again. The **Recipes** page needs no save at all.

> Note: the desktop "remembers your folder and auto-refreshes" convenience only exists in desktop Chrome/Edge. On iOS it's the quick upload above — which is exactly why syncing the save to OneDrive/Drive is the move.

## Credits
- totk-unexplored (map data, coordinates, icons), marcrobledo/savegame-editors (save format + icons), Zelda Wiki / Zelda Dungeon (armor + recipe data).

## Disclaimer
Fan project, not affiliated with Nintendo. Game assets (map imagery, icons) are © Nintendo and included for personal/reference use only.
