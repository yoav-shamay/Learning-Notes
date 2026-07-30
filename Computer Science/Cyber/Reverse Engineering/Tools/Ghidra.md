An open-source reverse engineering tool.
Make sure to open with linux for linux files.
## Tips
- Pressing F1 when hovering over an action will show an help menu
- F4 can allow you to set key binds.
- You can open Functions view (Window -> Functions) and then filter by name
- You can select the language, for example golang for go, for better decompilation.
## Projects
You can import files to a project by using File -> Import File, or by dragging and dropping.
## Code Browser
Allows you to view the disassembly and decompilation.
In the left there's symbols, selecting a function will move the disassembly and the compilation to the symbol.
If Ghidra doesn't detect automatically, try various symbols until you find the main function in order to begin.
### Navigation
Both the decompile and the disassembly show the same location.
When clicking on a symbol twice it will move to it.
You can go to a previous location by clicking the left arrow at the top left of the screen, or Alt + Left.
Similarly you can redo by clicking the right arrow there or Alt + Right.
In the middle / bottom left there's a symbol tree.
Clicking a function or symbol in it will move to it.
You can also press `G` and then type its name and press Enter.
### Decompilation editing
You can correct Ghidra decompilation on some cases and it will update the decompilation accordingly.
- You can rename a variable by right clicking it and selecting "Rename Variable".
- You can edit a function signature, including its return and input types by right clicking the function name in its declaration and selecting "Edit Function Signature".
- You can edit a variable type by right clicking it and selecting "Retype Variable".
- In the Data Type Manager you can right click a class and select "Edit" in order to edit its fields.
- To modify something to string, right click it in Listing view, select Data -> string
- If I reach an undefined function, find its beginning (click on first line, usually `endbr64` or some prologue) in listing view and click `F`
## Debugger
Start by pressing the bug button and select GDB.
Press start to launch the program.
There are the standard debugger controls:
Step Over - step 1 command. Will skip the subroutine when used in `call` instruction.
Step Into - step 1 command. Will step into the subroutine when used in `call` instruction.
Step Out - step out of current subroutine.
Resume - continue until next breakpoint.
### Putting breakpoints
In the decompiler window, you can right click a line and press toggle breakpoint / Set Breakpoint with `SW_EXECUTE`.
If it doesn't work, try after starting gdb and before `continue` to enable the breakpoint in the breakpoints listing.
### Using stdin and stdout
By marking `Inferior TTY` when starting the program, 2 terminals will be opened: 1 for gdb and 1 for interacting with the stdin and stdout of the program.
### Viewing variables
You can see absolute / relative address of a variable by going to a line that uses it in the decompiler, seeing the reference for it in the listing window and double clicking it there.
Then you can use this in the `gdb` terminal to print and see the value at this address (relative to `rsp/rbp` or absolute).
## Patching
### Modifying instructions
In code browser, in listing view, right click instruction and click "Patch Instruction".
TODO learn fully
### Modifying global
Find the global bytes in listing view, open bytes view (should open in same location), allow editing in the top bar, and now just type a new hex value.
### Export
Click File -> Export Program and select type to be `Original File`
### Fixing first-time error
run `python3 -m pip install psutil protobuf==3.20.3`.
https://interrupt.memfault.com/blog/using-pypi-packages-with-GDB  - ### Setting `sys.path` within `~/.gdbinit`
## Strings
### Viewing
TODO
### Searching
You can use `Search -> Memory` to search in the memory.
Other search options might also apply.