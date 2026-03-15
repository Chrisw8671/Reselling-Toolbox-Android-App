# Reselling-Toolbox-Android-App

A simple Android app that opens your website in a fullscreen `WebView`.

## 1) Change the website URL the app opens

Edit this file:

- `app/src/main/res/values/strings.xml`

Change:

```xml
<string name="web_app_url">https://100.92.48.58:3000/mobile</string>
```

to your real site, for example:

```xml
<string name="web_app_url">https://yourdomain.com</string>
```

> Use `https://` if possible. By default, cleartext (`http://`) traffic is blocked in `network_security_config.xml`.

---

## 2) Build an APK in Android Studio (easiest)

1. Install **Android Studio**.
2. Open this project folder in Android Studio.
3. Let Android Studio sync Gradle dependencies.
4. For a debug APK, go to:
   - **Build > Build Bundle(s) / APK(s) > Build APK(s)**
5. When build finishes, click **locate** in the notification.

Typical output path:

- `app/build/outputs/apk/debug/app-debug.apk`

---

## 3) Install APK on your phone

### Option A: direct file install

1. Copy `app-debug.apk` to your phone.
2. On phone, enable **Install unknown apps** for the app you use to open files.
3. Tap the APK and install.

### Option B: with USB + ADB

1. Enable **Developer options** and **USB debugging** on phone.
2. Connect phone via USB.
3. Run:

```bash
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

---

## 4) (Optional) Create a release APK for sharing

In Android Studio:

1. **Build > Generate Signed Bundle / APK**
2. Choose **APK**
3. Create/select a keystore
4. Choose **release** build type
5. Build

Release output is typically under:

- `app/build/outputs/apk/release/`

---

## Notes

- Internet permission is already enabled in `AndroidManifest.xml`.
- JavaScript and DOM storage are already enabled in `MainActivity`.
- Android back button goes back in webpage history before closing the app.

## Troubleshooting Gradle sync in Android Studio

If sync hangs/fails:

1. **Use JDK 17 in Android Studio**
   - `File > Settings > Build, Execution, Deployment > Build Tools > Gradle`
   - Set **Gradle JDK** to **Embedded JDK (17)** or any installed JDK 17.
2. **Disable Gradle Offline mode**
   - In the Gradle tool window, make sure Offline mode is OFF.
3. **Re-sync after repository fix**
   - This project now declares required repositories (`google()`, `mavenCentral()`, `gradlePluginPortal()`) in `settings.gradle.kts`.
4. **Try clean sync**
   - `File > Invalidate Caches / Restart` then sync again.

If it still fails, open **Build** output and copy the first red error line.
