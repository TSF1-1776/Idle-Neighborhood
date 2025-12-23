# Idle Neighborhood — Release Ready

**Release Date:** December 22, 2025

## What's included in this release

- Complete Godot 4.x prototype with core systems:
  - Idle income & offline earnings calculation
  - Grid-based lot expansion and building placement
  - Upgrade flow with popup UI
  - Ad and IAP stubs with plugin wrappers
  - Firebase analytics integration
  - Save/load persistence

- Production-ready documentation:
  - Full Game Design Document (GDD v1.0)
  - Publishing guides for Android & iOS
  - AdMob & Firebase plugin integration guides
  - IAP validation sample (Node.js)
  - Store listing templates & asset guides

- Helper scripts:
  - `push_to_github.ps1` — push to GitHub
  - `make_commits.ps1` — create grouped commits
  - `package_release.ps1` — package for release
  - `build_android.ps1` — export Android builds

- Store assets:
  - Icon templates (SVG 512x512)
  - Screenshot overlay templates

## Next steps

1. **Install Git** (if not already installed):
   - Download from https://git-scm.com/download/win

2. **Configure real Firebase & AdMob:**
   - Add real `google-services.json` and `GoogleService-Info.plist`
   - Add real Ad Unit IDs to `scripts/admob_plugin.gd`

3. **Test on device:**
   - Export to Android APK/AAB and test on device
   - Test iOS export on macOS with Xcode

4. **Push to GitHub:**
   ```powershell
   .\push_to_github.ps1 -remoteUrl "https://github.com/TSF1-1776/Idle-Neighborhood.git" -branch "main"
   ```

5. **Prepare for soft launch:**
   - Create store assets and screenshots
   - Test in TestFlight/Play Console internal testing
   - Soft launch in 1-2 regions
   - Monitor telemetry and iterate

## File structure

```
IdleNeighborhood-Godot/
├── project.godot              # Godot project config
├── scenes/                    # Scene files (Main, Buildings, GUI, UpgradePopup)
├── scripts/                   # GDScript files (main, building, grid, gui, wrappers)
├── assets/                    # Placeholder SVG sprites
├── DOCS/                      # Documentation (GDD, publishing, integration, store)
├── .github/workflows/         # CI/CD workflow
└── push_to_github.ps1         # GitHub push helper
```

## Delivery summary

✅ Complete cozy idle-builder prototype  
✅ All core systems (idle, offline, grid, upgrades)  
✅ Ad & IAP infrastructure (stubs + plugin wrappers)  
✅ Analytics integration (Firebase stubs + wrappers)  
✅ Full production documentation  
✅ Store asset & listing templates  
✅ CI/CD & release helpers  

Ready for device testing, real plugin integration, and store submission.
