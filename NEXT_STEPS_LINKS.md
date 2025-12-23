# Next Immediate Steps — Links & Commands

This file maps each immediate step to the exact code/docs in this workspace and provides the commands to run.

## 1) Install Git & push repository
- Why: Required to publish code to GitHub and enable CI.
- Files:
  - Repo push helper: [push_to_github.ps1](push_to_github.ps1)
  - Commit helper: [scripts/make_commits.ps1](scripts/make_commits.ps1)
  - Commit plan: [DOCS/GIT_COMMIT_PLAN.md](DOCS/GIT_COMMIT_PLAN.md)
- Commands (run after installing Git):

```powershell
# from the project folder
cd C:\workspace\IdleNeighborhood-Godot
# create grouped commits (inspect script first)
.\scripts\make_commits.ps1
# push to GitHub (HTTPS example)
.\push_to_github.ps1 -remoteUrl "https://github.com/TSF1-1776/Idle-Neighborhood.git" -branch "main"
```

Notes:
- If you prefer SSH, use `-useSsh` and the SSH remote URL.

## 2) Add Firebase credentials (Android + iOS)
- Why: Enable analytics and remote config; required for DebugView testing.
- Files to update/replace:
  - Example files to replace: [DOCS/Integration/google-services.json.example](DOCS/Integration/google-services.json.example), [DOCS/Integration/GoogleService-Info.plist.example](DOCS/Integration/GoogleService-Info.plist.example)
  - Plugin wrapper: [scripts/firebase_plugin.gd](scripts/firebase_plugin.gd)
  - Calls in game: [scripts/main.gd](scripts/main.gd) (analytics.log_event calls)
- Steps:
  1. Create a Firebase project and register Android & iOS apps.
  2. Download `google-services.json` and `GoogleService-Info.plist` from the Firebase console.
  3. Place `google-services.json` into the Godot project root and add `GoogleService-Info.plist` to the iOS Xcode project when exporting.
  4. Update `scripts/firebase_plugin.gd` or use `scripts/firebase_stub.gd` while testing.
- Test (DebugView):

```powershell
# Enable Firebase DebugView for Android (device connected via adb)
adb shell setprop debug.firebase.analytics.app <your.package.name>
# Launch the app and monitor events in Firebase DebugView
```

## 3) Add AdMob credentials & configure plugin
- Why: Enable rewarded ads and monetization.
- Files to update:
  - AdMob wrapper: [scripts/admob_plugin.gd](scripts/admob_plugin.gd)
  - Where ad events are used: [scripts/main.gd](scripts/main.gd), [scripts/building.gd](scripts/building.gd)
  - Plugin install guide: [DOCS/Integration/AdMob_Plugin_Install.md](DOCS/Integration/AdMob_Plugin_Install.md)
- Steps:
  1. Create an AdMob app and rewarded ad units for Android & iOS.
  2. Replace `ad_unit_android` and `ad_unit_ios` inside `scripts/admob_plugin.gd` with your production ad unit IDs (keep test IDs while testing).
  3. Install the chosen plugin (see `DOCS/Integration/AdMob_Plugin_Install.md`).
  4. Test ads on device and verify reward callbacks are fired.

## 4) Install AdMob & Firebase plugins in the project
- Why: Replace stubs with production SDKs.
- Docs:
  - [DOCS/Integration/AdMob_Plugin_Install.md](DOCS/Integration/AdMob_Plugin_Install.md)
  - [DOCS/Integration/Firebase_Plugin_Install.md](DOCS/Integration/Firebase_Plugin_Install.md)
- Typical steps:
  1. Copy plugin folder to `res://addons/` or follow plugin-specific install instructions.
  2. Enable the plugin in `Project -> Project Settings -> Plugins` in Godot.
  3. Update export templates / Gradle settings as the plugin requires.

## 5) Device testing & soft launch prep
- Why: Verify ads, purchases, analytics, and the user experience.
- Files / tools:
  - Build helper: [build_android.ps1](build_android.ps1)
  - Test flows in code: [scripts/iap_wrapper.gd](scripts/iap_wrapper.gd), [scripts/iap_server_validation.js](scripts/iap_server_validation.js)
  - Release packaging: [package_release.ps1](package_release.ps1), builds ZIP: [builds/IdleNeighborhood_prototype.zip](builds/IdleNeighborhood_prototype.zip)
- Steps:
  1. Create a signed Android AAB (or APK) using Godot export presets (configure keystore in Godot editor).
  2. Upload to Play Console internal track for testing.
  3. For iOS, export Xcode project, sign with provisioning profile, upload to TestFlight.
  4. Verify events in Firebase DebugView, verify ad watch flow and rewarded callback, perform test purchases using sandbox/test accounts.

## Quick file jump links
- Project summary: [PROJECT_SUMMARY.md](PROJECT_SUMMARY.md)
- Game design doc: [DOCS/GDD_v1.0.md](DOCS/GDD_v1.0.md)
- Main gameplay loop: [scripts/main.gd](scripts/main.gd)
- Building logic: [scripts/building.gd](scripts/building.gd)
- Grid manager: [scripts/grid.gd](scripts/grid.gd)
- GUI: [scenes/GUI.tscn](scenes/GUI.tscn) and [scripts/gui.gd](scripts/gui.gd)
- Upgrade popup: [scenes/UpgradePopup.tscn](scenes/UpgradePopup.tscn) and [scripts/upgrade_popup.gd](scripts/upgrade_popup.gd)
- Ad wrapper: [scripts/admob_plugin.gd](scripts/admob_plugin.gd)
- Firebase wrapper: [scripts/firebase_plugin.gd](scripts/firebase_plugin.gd)
- IAP stub: [scripts/iap_wrapper.gd](scripts/iap_wrapper.gd)
- Server validation sample: [scripts/iap_server_validation.js](scripts/iap_server_validation.js)

---

If you'd like, I can now:
- produce the exact `git` commands and a PR-ready commit sequence and run them for you once Git is installed, or
- walk you through installing the plugins step-by-step and update the wrappers to include your real AdMob & Firebase IDs.

Tell me which of those you want me to do next and I'll proceed.