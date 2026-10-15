# NovaCalc - How to Build Android APK Using ONLY Your Mobile Phone

This project is fully configured for Android APK export. You do **not** need a laptop or desktop computer to build your APK. Choose whichever method below is most convenient:

---

## METHOD 1: Instant APK via PWABuilder (Easiest - 2 Minutes)
*Zero terminal commands. Done 100% inside your Android phone browser.*

1. Open Chrome on your Android phone and visit the deployed app URL.
2. In Chrome, open **https://www.pwabuilder.com**
3. Paste the URL of your NovaCalc calculator app.
4. Click **"Start"** -> PWABuilder will test the PWA manifest and icons (all pre-configured!).
5. Click **"Package for Stores"** -> select **"Android"**.
6. Choose **"Download APK"** or **"Generate Package"**.
7. Your Android phone will download `NovaCalc.apk`. Tap it in your notifications to install!

---

## METHOD 2: Free Cloud APK Builder via GitHub (Recommended for Real APKs)
*This uses GitHub Actions in the cloud to compile a signed/debug Android APK for free.*

1. Extract this ZIP file on your phone (using Google Files or ZArchiver app).
2. Go to **https://github.com** on your mobile browser (sign in or create a free account).
3. Tap **New Repository** -> name it `novacalc-app` -> tap **Create**.
4. Tap **"Upload an existing file"** and select the extracted project files (including the `.github/workflows/build-apk.yml` file).
5. Tap **Commit changes**.
6. Go to the **Actions** tab on GitHub in your phone browser.
7. You will see the automated **"Build Android APK (NovaCalc)"** workflow running.
8. Once finished (~2 minutes), tap the completed run and scroll down to **Artifacts**.
9. Tap **"NovaCalc-Android-APK"** to download the `app-debug.apk` directly to your phone!

---

## METHOD 3: Build Directly on Phone Using Termux (On-Device Terminal)
*If you prefer running terminal commands directly on your Android phone:*

1. Install **Termux** from F-Droid (https://f-droid.org/packages/com.termux/).
2. Open Termux on your phone and run:
   ```bash
   pkg update && pkg upgrade -y
   pkg install nodejs-lts git openjdk-17 -y
   ```
3. Extract this project into Termux and navigate into the folder:
   ```bash
   cd novacalc-calculator
   npm install
   npm run build
   npx cap add android
   npx cap sync
   ```
4. Compile the APK:
   ```bash
   cd android
   ./gradlew assembleDebug
   ```
5. Copy the finished APK to your phone's standard Downloads folder:
   ```bash
   termux-setup-storage
   cp app/build/outputs/apk/debug/app-debug.apk /sdcard/Download/NovaCalc.apk
   ```
6. Open your Downloads folder on your phone and tap **NovaCalc.apk** to install!

---

## Included Features in NovaCalc:
- Complete arithmetic with PEMDAS precedence (+, -, *, /, %, ^, parentheses).
- Real-time live calculation preview as you type.
- Calculation history log with timestamps, search, reload formula, and reuse result.
- Web Audio API tactile mechanical clicks and vibration haptics.
- Responsive mobile layout with adaptive font sizing and gesture swipe-to-delete.
