edit `~/.bashrc` (using nano for example) and add this line to this end:
`export PATH="path/to/folder/bin:$PATH"`
Type `source ~/.bashrc` in the end to reload the shell.
You can also change PATH only for current session using `PATH="path1:path2:path3"`, and add folder to path using `PATH="/path:$PATH"`.