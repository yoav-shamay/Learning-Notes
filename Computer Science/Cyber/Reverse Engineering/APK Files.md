- APK files are actually zip files you can extract with 7-zip (or any other program)
## Decompilation
- You can decompile APK files to java using `jadx` (preferred method)
- You can convert APK files to jar files using `dex2jar` and then get source with `JD-GUI` for example.
- You can use `apktool` to disassemble APK files to smali and view XML and other utility files.
- Native functions exists in a library, can be extracted from `jadx` or `apktool` or just unzipping and decompiled using Ghidra.
## Viewing Resources
Strings, numbers and more
`Resources/resources.arsc/res/values/` - xml files there
If I can't find a string value in the code and instead a hex value it's probably there.
Can be viewed in jadx.
Also probably by unzipping or using `apktool`.
## Patching File
First, disassemble using `apktool`:
`apktool d app.apk -o app/`
Then make the changes on the smali or resources.
Then rebuild:
`apktool b app/ -o app.apk --use-aapt2`.
If there are problems try to disassemble using `-r` instead (partial disassembly), and don't add `--use-aapt2`
TODO find out how to edit it using Java if possible, maybe compilation to smali or smth.
## Signing APK file
A patched APK file needs to be signed for compiling.
It is done using the following procedure: (assumes input is in `app.apk`, output will be in `app-signed.apk`)
```bash
zipalign -f 4 app.apk app-aligned.apk
keytool -genkey -noprompt -dname 'CN=, OU=, O=, L=, S=, C=' -keystore apk.keystore -alias 'apk' -keyalg RSA -storepass 'password' -keypass 'password'
apksigner sign -out app-signed.apk --ks-key-alias 'apk' --ks apk.keystore --key-pass 'pass:password' --ks-pass 'pass:password' -v app-aligned.apk
```
Verify using `apksigner verify -v app-signed.apk`