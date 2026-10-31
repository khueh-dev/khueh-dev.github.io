# NINE Family Games catalog

Public catalog: **https://khueh-dev.github.io/family-games.json**

Apps with remote-catalog support fetch this file and cache it locally. Changes to this JSON and its icon files do not need a new app build. The Cube app revalidates the list automatically on opening the Family Games menu (with a five-second request throttle), and refresh stale lists after10 minutes while the menu stays open. The Cube menu has no manual refresh button. GitHub Pages deployment/CDN propagation can add a short delay.

## Add or update a game

Edit `family-games.json` in this repository and commit to the existing `main` branch. Add an icon under `family-icons/` if needed. Only public game information belongs in these files.

```json
{
  "version": 1,
  "games": [
    {
      "id": "blocks",
      "package": "com.studionine.ninetheblocks",
      "name": "NINE:theBlocks",
      "icon": "https://khueh-dev.github.io/family-icons/blocks-cf40e759720e.png",
      "order": 4,
      "enabled": true,
      "start": 0,
      "end": 0
    }
  ]
}
```

- `version`:1. Keep `games` as an array, with at most32 entries. An empty array intentionally hides all games.
- `id`: stable unique lowercase ASCII identifier,1–32 characters (`a-z`, digits, underscore). Do not reuse an old ID for another game.
- `package`: the exact Android package name. The app opens its Google Play listing and hides its own package.
- `name`: plain text,1–64 characters; no newlines/control characters.
- `icon`: optional HTTPS PNG URL on this same site under `/family-icons/`. Use an ASCII filename with letters/digits/underscore/hyphen. PNG only, up to512×512 and256KiB;256×256 is recommended. No query string, redirects or third-party icon URL.
- When changing an icon, upload a new filename (for example a content-hash suffix) and update `icon`. This avoids stale cached icons on existing devices.
- `order`: higher numbers appear first; identical order is sorted by ID.
- `enabled`: only set true after verifying the store page is available to the intended public audience. False hides a game without deleting its metadata.
- `start` / `end`: optional Unix timestamps in seconds;0 means no limit. End is exclusive and must be later than start when set. The app uses device time for visibility, not a trusted reward clock.

Malformed/unsupported/oversized lists are rejected as a whole and the app retains its previous good list. A failed icon uses the app's existing fallback icon. Offline devices show their cached list and cached icons, or the original bundled fallback if no cache is available.

This catalog controls promotion/listing only. It does not grant visit rewards, verify installations, change game rules or manage account balances. Existing homepage and `app-ads.txt` are independent of this catalog.
