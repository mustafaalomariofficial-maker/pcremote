# PC Remote

This repository hosts the supplied project archives and the GitHub Actions build for the Android APK.

## Android

The workflow downloads `PCRemote-Android-Project.zip` from the `source-v1` release, sets up JDK 17, Android SDK 34, and Gradle 8.2.1, then runs `assembleDebug`. The source archive includes Gradle wrapper properties but no wrapper script or wrapper JAR, so CI uses an explicit Gradle version. The app has minSdk 24 (Android 7.0+). Its README describes automatic PC search or entering the PC address and PIN.

## Windows package

`PCRemote-Windows.zip` is the original supplied package, published in the `source-v1` release. The source comments identify Windows 10 and Node.js 16 or newer; it has no npm dependencies. The phone and PC need the same local network. The agent prints its LAN address on port 8787 and a PIN; the panel is served at `http://PC_IP:8787`.

To start manually, extract the ZIP and run `start.bat` as Administrator. `install.ps1` also requests elevation, tries to install Node.js LTS, creates an elevated task at logon, and changes sleep/lid-close settings. The installer says first start uses “apps mode” and locks internet unless apps are allowed from the phone's Network tab. Review the scripts and these system changes before running them. The Windows package is a ZIP, not a tested single-file EXE.

## Testing and security

The source archives were scanned for common credential patterns; the scan found none. The Android APK build is checked by GitHub Actions. Neither package has been tested on the user's own phone and PC; check installation, local-network discovery, PIN login, and remote-control behavior there.
