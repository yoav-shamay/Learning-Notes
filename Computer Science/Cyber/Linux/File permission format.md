Text: `-rwxrwxrwx`
First character: `-` for file, `d` for directory
Group 1: `rwx` - read, write and execute for file owner
Group 2: `rwx` - read, write and execute for group owner of the file
Group 3: `rwx` - read, write and execute for all other users
(The letter is replaced with `-` to indicate that there is no permission)
Can be viewed with `ls -l`.
`chmod` uses a number which can be calculated with [[https://nettools.club/chmod_calc]]