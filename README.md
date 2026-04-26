🛡️ Blockify v1.0:
An ultra-reliable, system-level ad-nuke engine for Spotify, engineered specifically for HyperOS and MIUI devices.

Unlike standard ad-muters that just turn down the volume, Blockify uses a Hybrid Strike Engine powered by Shizuku to completely terminate the ad process and force-resume your music automatically. No root required.

🚀 Key Features
Hybrid Strike Engine: Uses package-targeted media dispatch (cmd media_session) with a global hardware interrupt fallback (input keyevent 79) to guarantee your music resumes.
Self-Healing Sensor: Defeats aggressive HyperOS background-killing by programmatically power-cycling the NotificationListenerService whenever the shield is armed.
Nuke & Resume: Employs a calculated 10-second stabilization window to allow the Spotify UI thread to reload before sending the resume command, preventing system race conditions.
Rootless Power: Uses Shizuku to execute ADB shell commands directly on the device locally and securely.
Battery Optimized: The core service only runs when the "Master Toggle" is armed, leaving zero footprint when you aren't listening to music.
⚙️ Prerequisites & Setup
Blockify requires a few specific Android Developer Settings to perform its hardware-level interrupts.

1. The Engine (Shizuku)
Blockify requires Shizuku to send system commands without root access.

Download Shizuku from the Play Store.
Start it via Wireless Debugging (You can turn Wireless Debugging off once Shizuku says "Running").
Open Blockify and grant Shizuku permissions.
2. The Core Settings (Developer Options)
To allow the app to send the "Play/Pause" hardware signal, you must grant it permission.

Go to Settings > About Phone and tap your OS Version 7 times to unlock Developer Options.
Go to Developer Options > Debugging.
Toggle ON the "Simulate touch" permission (Often bundled under USB debugging (Security settings) on Xiaomi devices).
📥 Installation
Go to the Releases page.
Download the latest app-arm64-v8a-release.apk (Recommended for modern devices like the Redmi 13C).
Install the APK and follow the in-app User Manual to arm the shield.
🛠️ Engineering Notes & Troubleshooting
Why is there a 10-second delay after skipping?
Analysis of chipsets like the Helio G85 showed significant UI thread latency during a cold start. The 10-second stabilization window ensures the Android MediaSession Registry is fully populated before the hardware interrupt is dispatched, guaranteeing a successful resume.

Why do I see two Blockify icons in my app drawer?
On Xiaomi/HyperOS, the system's "Dual Apps" feature may attempt to clone the app into a Work Profile. Blockify is restricted to the Primary User (User 0) for stability. You can safely disable the second icon in Settings > Apps > Dual apps.

The app is running, but it's not detecting ads!
HyperOS occasionally "blinds" background listeners to save RAM. Simply flip the Master Shield toggle OFF and then back ON. This triggers the Self-Healing Sensor to forcefully re-bind to the Android System Server.

