# Tarun's Songs — custom Mornye fork

This source tree contains initial customization work for a personal Android build based on the supplied Mornye 5.2.6 source archive.

## Changes in this fork

- Android launcher/application label changed to `Tarun's Songs`.
- Android application ID changed to `com.taruns.songs`, so it can be installed beside the original Mornye app.
- First tab now opens the first saved Subsonic connection directly when one exists. If there is no saved Subsonic connection, it falls back to the normal Home tab so the user can configure one.
- Added `.github/workflows/taruns-songs-apk.yml` for a manually triggered GitHub Actions arm64 Lite APK build.

## Build workflow

The workflow builds a Lite variant (`MORNYE_DISCORD_SDK=0`) to avoid requiring the separately staged Discord SDK. This is a build convenience; Discord-specific features will not be included. The workflow uploads an APK artifact if the build succeeds.

To run it, push this source tree to a GitHub repository you control, then open **Actions → Build Tarun's Songs APK → Run workflow**. Download the resulting `taruns-songs-android-arm64` artifact from the completed run.

## Important limitations

- The APK has **not** been compiled or device-tested in this workspace because Flutter, Rust, Android SDK/NDK, and network access to fetch dependencies are unavailable here.
- Existing Mornye secure storage is app-specific. The custom app will not automatically inherit the original app's saved server credentials; add the Subsonic connection once in Tarun's Songs. After that, this fork opens it directly.
- The direct-launch logic chooses the first saved Subsonic connection. If none exists, it falls back to Home.
- Review the upstream `LICENSE` and `COPYING` files before redistribution. This is intended as a personal fork.
