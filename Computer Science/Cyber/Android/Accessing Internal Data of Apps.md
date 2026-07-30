## Extracting APK
Enable [[USB Debugging]].
In `adb shell`, type `pm path package_name` like `adb path com.xyz.abc`
If I don't know, type `pm list packages` to get a list, can pipe and grep.
Then use (outside of shell) `adb pull <path>` (without the `package:` in the beginning, but everything there). It will download the APK to my computer. If there are multiple, do all of them (split APK).
## Enabling debugging
Extract the `apk` of the application somehow.
Now patch the app using [[APK Files#Patching File]]. Specifically, in `AndroidManifest.xml`, add in `<application>`: `android:debuggable="true"`.
Now reinstall the patched app.