# AttendPro

Attendance and payroll app with admin login. Works offline on Android.
Features: present, absent, half day, paid and unpaid leave, check in and check out,
automatic salary calculation, monthly sheet, payslips, Excel export, backup and restore,
admin login with auto lock.

## Get the APK (no coding tools needed)

1. Create a new repository on github.com (private is recommended).
2. Upload everything from this folder: `www/`, `.github/`, `package.json`,
   `capacitor.config.json`, `.gitignore`, `README.md`.
   Make sure the `.github/workflows/build-apk.yml` path is kept exactly.
3. Open the **Actions** tab. The workflow **Build Android APK** starts by itself
   after the upload (or press **Run workflow**). It takes about 5 to 8 minutes.
4. Open the finished run, scroll to **Artifacts**, download **AttendPro-APK**,
   unzip it and install `app-debug.apk` on your phone
   (allow "Install unknown apps" when asked).

## First use

- On first launch the app asks you to create the admin username and password.
- Only that login opens the app. It locks itself after 5 minutes (changeable in Settings).
- Download a backup regularly: Settings & backup > Download backup.

## Security notes

- Data and the password hash are stored on the phone, inside the app. Other apps cannot read them on a normal phone.
- It is a local lock, not a server login. A person who has your unlocked phone or a rooted device could get around it.
- The password cannot be recovered. If you forget it, "Forgot password" erases all data. Keep backups.

## Change the app name, id or icon

- App name and id: edit `capacitor.config.json`.
- Icon: add `resources/icon.png` (1024x1024) and run `npx @capacitor/assets generate --android` locally before building.

## Run on a computer (optional)

    npm install
    cp node_modules/xlsx/dist/xlsx.full.min.js www/
    npx serve www

## Known limits

- Print buttons do not work inside the Android app. Use Export to Excel, or share the file and print from there.
- The APK is a debug build, fine for your own use. A Play Store release needs a signed release build.
