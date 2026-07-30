A command line tool suite for analyzing disk images.
You can use `mmls img` to get the offsets of each partition.
Then, you can use `fls -r [-o <offset>] <img>` to list files (r = recursive, offset = partition offset given from previous command)
You can extract files using `icat [-o <offset>] <img> <num>` where num is the number given in fls.
You can search for printable strings in files: `srch_strings [-f] <img> | grep [-i] <text>`. 
`-f` to show file name before each string
`-i` on grep ignores case