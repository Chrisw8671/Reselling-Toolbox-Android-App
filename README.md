# Reselling-Toolbox-Android-App

This repository now contains a minimal Android WebView app that opens your website in fullscreen.

## How to use

1. Open `app/src/main/res/values/strings.xml`.
2. Replace `web_app_url` with your website URL.
3. Build and run the app from Android Studio.

## Notes

- JavaScript and DOM storage are enabled for modern web apps.
- Back button navigation works inside the `WebView` history.
- Internet permission is already configured in `AndroidManifest.xml`.
