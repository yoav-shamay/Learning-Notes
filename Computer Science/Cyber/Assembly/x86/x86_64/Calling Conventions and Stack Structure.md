caller - who called the function
callee - the called function.
Top of the stack - lower addresses
Bottom of the stack - higher addresses
`push` - decreases `rsp`
`pop` - increases `rsp`
### Passing Arguments
first 6 arguments - registers: `rdi`, `rsi`, `rdx`, `rcx`, `r8`, `r9`
Other arguments are passed in the stack in reverse order (lowest address - first argument)
### Conventions
The callee should preserve the values of `rbp`, `rbx`, `r12`-`r15`
The return value is placed in `rax`.
The callee should clean up the local variables and the return address from the stack
The stack must be aligned to a 16-byte boundary **before** the call instruction.
The caller should place and cleanup the arguments pushed in the stack (placing - usually by pushing, cleaning up - usually by just subtracting the size from `rsp` after the call.).
Before calling variadic function (unknown arguments), you should set `rax` to 0. This is because `rax` specifies how many SSE registers are passed and this is usually 0.
### Callee first instructions (before the function itself)
```asm
push rbp ; push old rbp to the stack
mov rsp,rbp ; save rsp to rbp, this is the current stack bottom
sub <space allocated to local variables>, %rsp ; rsp now points to the top of the local variables
```
This is also equivalent to the following:
```asm
enter <space allocated to local variables>, 0
```
Though the second option is rarely used in compilers.
### Callee last instructions (at the end of the function itself)
```asm
mov rbp, rsp ; save rbp to rsp, restoring its previous value
pop rbp ; restore previous rbp
ret ; return from the function, popping the return address and jumping to it
```
This is equivalent to the following:
```asm
leave
ret
```
The leave instruction is equivalent to moving rbp to rsp and popping rbp.
### Stack structure (top - low addresses, bottom - high)
- rsp points here (below all local variables)
- Local variables
- rbp points here (top of local variables)
- Saved rbp
- Return address
- first stack argument
- ...
- last argument
### Function-call related instructions
- `call address` instruction: pushes the return address to the stack, and jmp to the address specified
- `ret` instruction: pops the return address from the stack, and jmp to this address. `ret num` after returning increments `rsp` by `num` (skipping this number of bytes in the stack, used for arguments cleanup)
- Note that `push` and `pop` instructions uses `rsp`, not `rbp`.
- `enter size, 0` instruction: pushes `rbp` (usually of the caller), places `rsp` to `rbp` (moving `rbp` to the actual current function stack base) and subtracts the size from `rsp` (moving it to the top of the local variables).
- `leave` instruction: moves `rbp` to `rsp` (basically removing local variables), and pop `rbp` (usually after the previous function `rbp` is placed there at the beginning)
### Function call process
Before call:
- `rbp` points to the bottom of the caller's local variables and `rsp` to the top.
During call:
- All stack parameters are pushed, the first one at the top.
- Return address is pushed to the stack, now `rsp` points above it.
- The code jumps for the function
- Previous base pointer is pushed. the base pointer is moved to the current top of the stack, and the stack pointer is moved up by the space allocated to local variables.
- Now `rbp` points to the start of the local variables and `rsp` to after them. Note that `rbp` is usually used to access local variables and parameters, rsp only for pushing and popping.
At function leave:
- `rsp` is changed back to `rbp`, effectively removing all local variables (ignoring them).
- The previous `rbp` value is popped, restoring the `rbp` of the caller.
- The return address is popped and the code jumps to it.
- `rbp` points to the caller's `rbp` and `rsp` points to the caller's top of the stack (because parameters and saved `rbp` are popped).
- We're back at the caller, all stack-pushed parameters are popped and the caller's state is restored.