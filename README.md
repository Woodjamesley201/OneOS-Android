# OneOS for Android

Native Android app that runs [OneOS](app/src/main/assets/OneOS.html) — a single, self-contained HTML file — inside a full-screen WebView.

The original `OneOS.html` is bundled **unmodified** as an app asset (`app/src/main/assets/OneOS.html`) and loaded directly by a thin wrapper activity. No changes are made to the file.

## APK

Prebuilt, signed APK: [`dist/OneOS-v1.0.apk`](dist/OneOS-v1.0.apk) (also attached to [GitHub Releases](../../releases)).

- Package: `com.oneos.app`
- Version: 1.0
- Min Android: 7.0 (API 24) · Target: Android 14 (API 34)
- Size: ~0.9 MB

## Install

1. Download `OneOS-v1.0.apk` on your Android device.
2. Open it and allow "Install from unknown sources" if prompted.
3. Launch **OneOS** from your app drawer.

## Build from source

Requires JDK 17 and an Android SDK (platform 34, build-tools 34).

```bash
export ANDROID_HOME=/path/to/android-sdk
gradle assembleRelease
# Output: app/build/outputs/apk/release/app-release.apk
```

The release build is signed with `keystore/oneos-release.keystore` (alias `oneos`).

## Project layout

```
app/src/main/
├── assets/OneOS.html        # the unmodified OneOS web app
├── java/com/oneos/app/MainActivity.java   # WebView wrapper
├── res/                     # launcher icons, theme, strings
└── AndroidManifest.xml
```

## Notes

- The WebView has JavaScript, DOM storage, and database support enabled so the web app behaves as it does in a browser.
- The Back button navigates WebView history when possible.
- The signing keystore is committed for reproducible builds since this repo is private — replace it before any public distribution.
