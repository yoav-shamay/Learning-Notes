`ltrace` can easily show function calls and how many input is read in a program.
Only works on dynamically linked binaries.
Simply use `ltrace <binary>`, and it will print every function and library call done.

In addition, it won't read more from stdin than the program reads, so it allows seeing how many characters are read by seeing how many are read in the end.