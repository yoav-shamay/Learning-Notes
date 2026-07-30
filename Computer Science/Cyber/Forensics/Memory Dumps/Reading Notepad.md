In case of multiple processes, it's most likely in the bottom one in the children chain (the one with no further children).
## Method 1 - strings
Run `strings -el` and try to find something noteworthy.
`strings -el` due to the UTF16 format.
Try `grep` for the word `flag` / flag format.
Note that finding text in the `notepad` doesn't guarantee it's actually typed in it, there's a lot of leftover data from other processes.
## Method 2 - Using the heap (most reliable)
As in https://hackmd.io/@trongtam21/HkxqYQtmge
Open the process memory in [[WinDbg]] .
See all heap chunks `!heap -s -v -a`
Then search (using Ctrl + F) regions with the "extra" flag on.
Specifically, it should have `busy extra user_flag`.
It will be most likely on the first region.
Try on each region to inspect its memory using `db <second entry> L80` (increase the `80` to the amount of bytes you want).
The content should be there in UTF-16 little endian, right at the beginning.
## Method 3 - Using VADs
Probably worse than heap.
You can extract only data in VADs to reduce the search space, and manually search strings in them.
Dump all the VADs and search strings in them.
`vol -r json -o vads -f chall.raw windows.vadinfo --pid <pid> --dump > vads.json`
Tou can further filter only vads with permissions PAGE_READWRITE:
```python
import json
f = open("vads.json")
text = f.read()
f.close()
parsed = json.loads(text)

for entry in parsed:
    if entry["Protection"] == "PAGE_READWRITE":
        file_name = entry["File output"]
        print(file_name)
        with open(file_name, "rb") as f:
            data = f.read()
        with open("filtered/" + file_name, "wb") as f:
            f.write(data)
```
It might be adjacent to `Untitled`.
Run `strings -el * > strings.txt` in the directory, and search for strings.
TODO remove? unsure if useful
## Method 4 - volatility2 notepad plugin
Just use the `notepad` plugin.
Doesn't work in most profiles
## Windows 11
https://dfir.pubpub.org/pub/wmhy8t6v/release/6
TODO