# Deployment helper (generated)

Files created/updated:
- package.json (cleaned)
- app.json (created/updated with placeholder package name `com.myapp.app`)
- eas.json (build & submit profiles)
- .github/workflows/eas-build.yml (CI workflow with optional submit)

## What I changed in package.json
- Removed Replit-specific `dev` script and proxy environment variables.
- Added clean scripts: `start`, `android`, `ios`, `web`.
- Adjusted core versions for Expo SDK 54 compatibility:
  - react -> 18.2.0
  - react-dom -> 18.2.0
  - react-native -> 0.73.6
  - react-native-reanimated -> ~3.10.0
- Updated dev dependency `@types/react` to ~18.2.0

## Important next steps (you must do these locally)
1. **Replace the Android package name** in `app.json` if you want a different one:
   - Current placeholder: `com.myapp.app`
   - Choose a reverse-DNS name like `com.yourcompany.myapp`.

2. **Install dependencies & create lockfile:**
   ```bash
   npm install
   git add package-lock.json
   git commit -m "Add package-lock.json"
   ```

3. **Run interactive EAS configure (first-time, local)**
   ```bash
   expo login
   npx eas-cli@latest build:configure
   # or
   eas build:configure
   ```

4. **Build once interactively to set credentials**
   ```bash
   npx eas-cli@latest build --platform android --profile production
   # After successful interactive build, CI can use --non-interactive
   ```

5. **Configure GitHub secrets (if using CI automated builds)**
   - `EXPO_TOKEN` — create with `npx eas-cli@latest token:create` after `expo login`
   - (Optional) `GOOGLE_SERVICE_ACCOUNT_JSON` — full JSON key contents if you want `eas submit` to upload to Play automatically.

## Notes
- This environment could not run `npm install` — you must run it locally to generate `package-lock.json`.
- If your project layout uses a subfolder for `package.json`, update the workflow's steps to `cd` into that folder before `npm ci` and `eas build`.

