Requires the phone to be plugged by USB.
Enable in the phone developer settings "USB Debugging".
Then install ADB on the machine.
Type `adb devices` and allow permission on the phone if it says `unauthorized`.
## Shell
Type `adb shell` to get a shell.
Options:
`pm list packages` - list of packages
`pm path com.package.name` - get path of package name
TODO organize and a bunch of options
## Downloading files
`adb pull <phone path>` - download a file, including hidden ones (TODO details).
