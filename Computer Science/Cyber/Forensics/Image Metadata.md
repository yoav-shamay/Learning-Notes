- Viewing: `exiftool image.jpg`
- Modifying: `exiftool image.jpg "-Property=Value"`. For example: `exiftool image.jpg "-DateTimeOriginal=1970:01:01 00:00:00.01+00:00"`
## Metadata Available
- `ImageDescription` - might be called `caption`
### Timestamps
- `ModifyDate`, `SubSecModifyDate`
- `CreateDate`, `SubSecCreateDate`
- `DateTimeOriginal`, `SubSecDateTimeOriginal`
- `Samsung:Timestamp`. Note that this one needs to be edited in a hex editor. Find the hex dump of `Image_UTC_Data` (49 6d 61 67 65 5f 55 54 43 5f 44 61 74 61) and replace the following 13 bytes with the timestamp. (details in https://stackoverflow.com/questions/78185037/how-to-edit-the-samsung-trailer-tag-timestamp).