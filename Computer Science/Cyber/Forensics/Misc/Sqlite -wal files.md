Write ahead log files.
Contains data about operations performed in the DB before they are actually saved in disk.
DB browser for sqlite automatically applies them when opening the DB.
Can both add and delete records.
To analyze, open it once with the `-wal` file present and once without (in a different folder as the merge overwrites it).
That will allow you to access both deleted and inserted records.
Does not give all theoretical data, but couldn't find any way to do it (TODO).