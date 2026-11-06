# NINE:theBounce update policy

Public file: **https://khueh-dev.github.io/bounce-app-policy.json**

NINE:theBounce versions that run without the game server read this file on the intro screen. Versions that still use the
game server read the same fields from the server instead, so this file does not affect them.

- `configKey` stays `android_version_policy`.
- `androidMinVersionCode`: an installed version code below this shows the update screen and START stays closed.
- `androidRecommendedVersionCode`: never below the minimum (a file with a smaller value is ignored).
- `androidStoreUrl`: the app's Google Play page (`https://play.google.com/store/apps/details?id=com.studionine.ninethebounce`).
- `forceUpdateTitleKo`, `forceUpdateMessageKo`, `forceUpdateTitleEn`, `forceUpdateMessageEn`: the update screen's text.
- `androidMinVersionName`: the minimum version's name, for people reading the file.

Version codes are JSON numbers. Keep the file a flat object of strings and numbers, under 8 KB. A file the app cannot read,
or no network, never stops play: only a file that was read and names a newer minimum does. GitHub Pages can take a few
minutes to serve a change.
