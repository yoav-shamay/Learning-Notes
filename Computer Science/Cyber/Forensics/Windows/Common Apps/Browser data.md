## Where to find
### Edge
Saved in `C\Users\khaled.allam\AppData\Local\Microsoft\Edge\User Data\Default`
The `History` file is a sqlite database containing visited URLs, downloads, and more.
### Chrome
Saved in `C:\Users\username\AppData\Local\Google\Chrome\User Data\Default`
- The `History` file is a sqlite database containing visited URLs, downloads, and more.
- Version is saved in `C:\Users\username\AppData\Local\Google\Chrome\User Data\Last Version` (as text)
### Firefox
Saved in `C:\Users\username\AppData\Roaming\Mozilla\Firefox\Profiles\<profile>`
The `places.sqlite` is a database containing browsing history, downloads and bookmarks.
URL History is in `moz_places`, downloads are in `moz_annos`.
Login data is saved in `logins.json` and `key4.db`.
Can be decrypted using https://github.com/lclevy/firepwd: `python firepwd.py -d /path/`
## Opera
Saved in `C:\Users\username\AppData\Roaming\Opera Software\Opera Stable`
The `History` file is a sqlite database containing visited URLs, downloads, and more.
## Naver Whale
Saved in `C:\Users\username\AppData\Local\Naver\Naver Whale\User Data\Default`
The `History` file is a sqlite database containing visited URLs, downloads, and more.
## Timestamps
saved in special format - microseconds since January 1st, 1601 00:00 UTC
converter - https://www.epochconverter.com/webkit