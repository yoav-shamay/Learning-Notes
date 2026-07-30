Windows timeline database
Contains data about processes run, clipboard data and more.
An sqlite database.

Might also come with a [[Sqlite -wal files|-wal file]] so should want to backup the original file before opening. Try to open both with the `-wal` and without it (in different folders).
## Data
- Clipboard data - Clipboard Payload column in `ActivityOperation`.