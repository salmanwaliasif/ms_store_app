# MS Store Oman - Flutter WebView App

A simple, clean Flutter app that loads shop.msstoreoman.com inside a native shell.

## What This App Does
- Shows a branded splash screen on launch
- Loads shop.msstoreoman.com in a full-screen WebView
- Handles no internet / errors with a retry screen
- Back button navigates browser history, then shows exit dialog
- Progress bar shows page loading

## Setup (5 Steps)

### 1. Install Flutter
Download Flutter SDK from https://flutter.dev
Make sure `flutter doctor` passes with no errors.

### 2. Get the code ready
```bash
cd ms_store_app
flutter pub get
```

### 3. Add your app icon
- Replace `assets/icon/icon.png` with your MS Store logo
- Must be at least 1024x1024px, PNG format
- Run: `flutter pub run flutter_launcher_icons`

### 4. Run on your phone
- Enable Developer Mode + USB Debugging on your Android phone
- Plug in via USB
```bash
flutter run
```

### 5. Build release APK
```bash
flutter build apk --release
# Output: build/app/outputs/flutter-apk/app-release.apk
```

## Customization

| What to change | Where |
|---|---|
| Store URL | `lib/webview_screen.dart` → `_storeUrl` |
| App name | `android/app/src/main/AndroidManifest.xml` → `android:label` |
| Splash colors | `lib/splash_screen.dart` → Color hex values |
| Package ID | `android/app/build.gradle` → `applicationId` |
| App version | `pubspec.yaml` → `version` |

## Color Scheme
Primary dark: `#1A1A2E`
Change this in `main.dart`, `splash_screen.dart`, and `webview_screen.dart`

## Publishing to Google Play
1. Create a keystore: `keytool -genkey -v -keystore ms-store.jks -alias ms-store -keyalg RSA -keysize 2048 -validity 10000`
2. Configure signing in `android/key.properties`
3. Build: `flutter build appbundle --release`
4. Upload `build/app/outputs/bundle/release/app-release.aab` to Play Console
