Instead of computing where symbol points to for external function calls at program startup, you do it when it's called.
When a function is called, it gets to the `.plt` section.
The first time it's called, the destination address gets resolved.
On subsequent calls it jumps directly to it.
The address is saved in the `.got` section and it jumps to whatever address written to it. With partial RELRO (almost always) It can be overridden for exploits.
## `.plt` section
In the `.plt` section, there's three instructions for each function. the first one is a `jmp` instruction.
Before resolution it will point to the next instruction, afterwards directly to the resolved address.
### Resolution
When calling an unresolved function in the `.plt`, the GOT section will point to the next line, which includes those instructions:
```assembly
push <reloc_index>
jmp <head of plt>
```
`reloc_index` is a number which indicates the function called - `0x0` for the first function in the `.plt`, `0x1` for the second one and so on.
Note that parameters are passed in the stack as the registers already contain the parameters of the called function (`puts` for example)
Then it always jumps to the head of `.plt` which contains those instructions:
```assembly
push <second entry of got - link map head address>
jmp <third entry of got - _dl_runtime_resolve location>
```
so it pushes another argument which is the address of the link map head, the second entry in the GOT table.
Then it finally jumps to `_dl_runtime_resolve`, which its address is the third entry in the GOT table.
## `.got.plt` section
The top 3 entries of the `.got.plt` section contains the following:
- the address of the `.dynamic` section
- the linkmap's head
- the address of `_dl_runtime_resolve()`
All further entries are functions that will be resolved (points to the corresponding `push; jmp;` instructions at the `.plt` section in initialization).
## The `.dynamic` section

## The `_dl_runtime_resolve` function
This function is part of the dynamic linker (`ld-linux`).
In short, it does the following things:
- Finds a NULL terminated string of the target function name
- Search it in all loaded libraries and finds its address
- Write the address in GOT
- Jumps to this address.
In more details:
As seen in [[#Resolution]], it receives 2 parameters - address of link map and the reloc index.