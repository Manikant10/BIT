# Expo/EAS Deployment helper (auto-generated)

Files added/updated:
- eas.json
- .github/workflows/android-build.yml


## What I added
- `eas.json` (build profiles production=AAB, internal=APK)
- GitHub Actions workflow `.github/workflows/android-build.yml` that runs `eas build` on pushes to `main`.
- `app.json` created/updated to include `expo.android.package` (if detected from AndroidManifest or build.gradle).

## Secrets required for CI
Add these GitHub repository secrets:
- `EXPO_TOKEN` — create with `expo token:create` after `expo login`.
- (Optional, to auto-submit to Play) `GOOGLE_SERVICE_ACCOUNT_JSON` — the JSON contents of a Google Play service account key. If you add this secret you can enable `eas submit` in the workflow.

## Important manual step
If this is your first Play Console upload, you may need to create the app in Play Console and upload the first AAB manually (store listing, content rating, privacy policy). After that, `eas submit` and CI automated submit will work more smoothly.

## Notes
- none
