# GetTok updates

The GetTok app reads [`update.json`](update.json) on launch and whenever it returns to the foreground. If the installed version is lower than `minVersion`, it shows the **Update required** screen and can't be used until the user updates.

## Shipping a new version

1. Build the APK with a higher `version` in the app's `app.json`.
2. Create a Release in this repo and attach the APK.
3. Edit `update.json`:
   - `minVersion`: the version users must have (set it to the new version to force everyone onto it)
   - `latestVersion`: shown on the badge and footer
   - `url`: where **Update now** goes; `releases/latest` always points at the newest Release
   - `size`, `message`, `notes`: shown on the update screen (`notes[].icon`: `lightning`, `stack`, `shield`, `sparkle`, `bug`, `download`, `star`)

GitHub can serve the old copy of `update.json` for a few minutes after an edit.

Keep `minVersion` at or below the version people already have until the new APK is uploaded; otherwise everyone gets blocked with nothing to update to.
