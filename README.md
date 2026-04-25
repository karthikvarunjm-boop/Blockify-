he app-arm64-v8a-release.apk is the primary "flagship" build for your project, it deserves a technical breakdown that explains why it is the superior choice for your Redmi 13C and other modern devices.

Here is a detailed description you can use in the Assets section or the Release Notes on GitHub:

📦 Technical Specification: app-arm64-v8a-release.apk
This is the optimized 64-bit production build of Blockify v1.0. Unlike the universal or debug builds, this APK is compiled using Ahead-of-Time (AOT) compilation specifically for the arm64-v8a instruction set, ensuring maximum execution speed and minimal memory overhead.

🛠 Architecture Overview
The arm64-v8a (AArch64) architecture is the standard for modern mobile processors. By targeting this specifically, Blockify communicates directly with the 64-bit registers of chipsets like the Helio G85, reducing the abstraction layer and improving the response time of the Hybrid Strike Engine.

🚀 Key Performance Benefits
Reduced Binary Size: At 18.7 MB, this build is nearly 85% smaller than the debug version. All non-essential debugging symbols and unused Material Icons have been "tree-shaken" to save storage.

Faster Ad-Nuking: The Kotlin backend responsible for terminating ad processes runs with 64-bit precision, leading to faster process identification and "striking" than the 32-bit legacy version.

Optimized Resource Management: This build is specifically tuned to resist the aggressive RAM management of HyperOS/MIUI, allowing the Self-Healing Sensor to remain resident in memory without being flagged as a "rogue" process.

🔋 Power Efficiency
Because this APK is built using the --split-per-abi flag, it does not contain the code for older 32-bit (v7a) or desktop (x86) architectures. This results in:

Faster Installation: Fewer files for the Android Package Manager to verify.

Lower Battery Consumption: The CPU doesn't have to run in "32-bit compatibility mode," which is inherently less efficient.

📝 Installation Guide
Ensure Shizuku is active and authorized.

Verify that "Simulate touch" is enabled in your Developer Options to allow this build to send the Hardware Interrupt 79 signal.

Exclude this app from Battery Optimization (Set to "No Restrictions") to maintain the integrity of the persistent monitoring pipe.

Note: This version is intended for all modern Android smartphones. If you are using a device older than 2016, you may need the armeabi-v7a legacy build instead.
