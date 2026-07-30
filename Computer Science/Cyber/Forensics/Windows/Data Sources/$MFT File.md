Has metadata about all files, like timestamps, and their physical location in disk.
Can contain the entire content of small files.
Can also contain some deleted files or some older versions of existing files.
Can be analysed using:
- MFTExplorer (from https://ericzimmerman.github.io/#!index.md)
- `analyzemft -f '$MFT' -o results.json --json` (install using `pip install analyzeMFT`)