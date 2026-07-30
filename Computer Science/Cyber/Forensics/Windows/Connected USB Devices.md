## From Registry Entries
- General connections - `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USB`
- Specifically flash drives - `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR`
Info that can be deduced:
- The Serial Number of the device is the name of the inner directory of this specific device (there's general name -> serial number), including the `&` in the end.
- The plug time is the earliest "last modify date" of all the entries. It's in the original device's timezone.