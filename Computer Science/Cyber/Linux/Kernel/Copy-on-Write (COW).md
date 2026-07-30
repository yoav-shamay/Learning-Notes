When you open a file, the kernel loads it to the RAM.
However, as many process might use this file, the kernel uses a Copy-on-Write concept.
At first, all the virtual addresses will point to the same physical memory when the file was first loaded.
When some program attempts to write there, the kernel will copy the entire content to another location in the physical memory, and then changes the virtual memory to there.
Then the program will write on the copied data.