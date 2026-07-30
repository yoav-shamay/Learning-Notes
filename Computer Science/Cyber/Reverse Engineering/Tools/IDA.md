A reverse engineering tool.
## Resetting Layout
in case I closed something
`Window -> Reset Desktop`
## Creating / editing structs
Go to local types tab. if closed `View -> Open Subviews -> Local Types`
Then right click, choose `Add Type`.
Go to the `C syntax` tab.
Might need to refresh decompilation after editing.
## Viewing imported (dynamically linked) / exported functions
Imports - `View -> Open subviews -> Imports`.
Very useful as initial look.
Exports - `View -> Open subviews -> Exports`
Useful for `.dll` / `.so` files.
## Keyboard Shortcuts
- Refresh / open decompilation - `F5`
- Swap decompilation / disassembly - `tab`
- Swap graph / normal view - `Space`
- Rename variable / label / create label - `N` when hovering address / variable
- Change variable type / function signature - `y`
- View XREFs - `X`
- Go to Next / Prev variable reference - `Alt + Up` / `Alt + Down`
- Turning symbol to function - `P`, Might require to turn it to raw bytes and reassemble it for IDA to treat it as a separate function.
- Start disassembly from location - `C` when in location
- Change assembly to raw bytes - `U`, Can be useful to split part of a function to another function.
- Show number as char - `r`
- Number decimal <=> hex - `h`
- Convert byte sequence to string - `a`
- Defining byte as data - `d`
- Defining bytes in data as array - `*`
## Debugger
### Breakpoints
Breakpoints can be put in either assembly / decompilation by right clicking a line and selecting add breakpoint.
### Remote debugging
The executables directory is `~/idapro-9.0/dbgsrv` in linux.
Run either `win64_remote64` for windows, or `linux_server64` for linux.
Pass `-p23946 -Ppass`.
Select host `localhost`, port `23946`, password `pass` in IDA debugger config.
Will open a console that allows typing stdin / stdout, so useful if access for it is needed as IDA normal debugger doesn't support.
#### Troubleshooting
- If movement functions cause problems, disable hardware temporary breakpoints in `Debugger -> Debugger Options -> Use hardware temporary breakpoints`
### Enabling controls toolbar
Press `View -> Toolbars -> Debugger Commands`
New toolbar with controls will open.
### Evaluation Expression
The best way is to use `Watch View`, can open using `Debugger -> Debugger Windows -> Watch View`. Then type any expression.
Alternatively, for quick evaluation, press `Shift + /` (`?`).
Can use register names (like `rsp + 0x100`)
Also understands variable names from decompilation.
Dereferencing memory: 
- `get_qword/get_dword/get_word/get_byte(address)`
- `Qword/Dword/Word/Byte(address)`
- `get_strlit_contents(address, -1, STRTYPE_c)` - read string at address
- Watch view will automatically show the value at this location if it's a string.
Note that the `Location` column will show addresses / offsets (such as `esp + smth`) in hex. for example `esp + 24` means `esp + 0x24`.
## Patching
Use `Edit -> Patch program -> Assemble` and type a new instruction
Alternatively select `Change byte` to patch raw bytes.
In the end select `Apply patches to input file`. 
Probably want to check "Create backup".
### Function calls
IDA assembler might not interpret symbols correctly when doing `call <symbol>`
In this case you can manually patch the bytes to make the correct call.
Can just use `call 0xoffset` in any assembler such as [[Online Assembler and Disassembler]], offset can be negative.
In case of PIE binaries it might still not work due to relocation changing the bytes at runtime, in this case it might be needed to patch during runtime by debugging.
## Decompiler special functions
The definitions are located in `ida-install-dir/plugins/hexrays_sdk/include/defs.h`
- `HIBYTE` - highest value byte
- `LOBYTE` - lowest value byte
## Copying area from hex view
Normal selection uses rectangles and can be annoying from middle of row
- Select start byte.
- Select Edit -> Begin Selection
- Select end byte
- Select Edit -> Export Data
Don't worry if it shows weird rectangle, it will export the correct data.
## Fixing IDA disassembly/decompilation
### Creating data array (prevent data split)
if for some reason IDA detects wrongly a global array size and splits it in multiple variables, changing the type might won't be enough.
In this case (maybe) undefine the data using `U`, define it as data of the right width using `d`, and set as array using `*`, specifying the size.
### Changing function stack size
In some cases IDA might misdetect the stack size of the function.
For example, on certain "leaf" functions that call no other functions, the compiler omits the `sub rsp, xyz` instruction, confusing IDA.
A common sign for this is a `savedregs` variable where IDA references `*(&savedregs - x)`
In this case, open the function in listing view, press `Alt + P`, and change `Local variables size`.
Afterwards refresh decompilation using `F5`
### Splitting / Merging stack variables
Changing the datatype of a variable in stack to a datatype with different width will automatically adjust the stack detection accordingly.
