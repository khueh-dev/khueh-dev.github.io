# NINE:theDirection update policy

Public file: **https://khueh-dev.github.io/direction-app-policy.json**

NINE:theDirection versions that run without the game server read this file on the intro screen. Versions that still use the
game server read the same fields from the server instead, so this file does not affect them.

- `configKey` stays `android_version_policy`.
- `androidMinVersionCode`: an installed version code below this shows the update screen and START stays closed. `0` means no minimum.
- `androidRecommendedVersionCode`: never below the minimum (a file with a smaller value is ignored).
- `androidStoreUrl`: must be exactly `https://play.google.com/store/apps/details?id=com.studionine.ninethedirection`; any other value makes the app ignore the file.
- `forceUpdateTitleKo`, `forceUpdateMessageKo`, `forceUpdateTitleEn`, `forceUpdateMessageEn`: the update screen's text.
- `androidMinVersionName`: the minimum version's name, for people reading the file.

Version codes are JSON numbers. Keep the file a flat object of strings and numbers, under 8 KB. A file the app cannot read,
or no network, never stops play: only a file that was read and names a newer minimum does. GitHub Pages can take a few
minutes to serve a change.
