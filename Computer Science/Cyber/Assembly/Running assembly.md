## In C
You can insert assembly in C files, using inline assembly, the `asm` keyword.
Syntax:
```c
asm("line1\n"
	"line2\n"
	"line3\n"
);
```
I can also replace `\n` with `;`.
This uses AT&T syntax by default.
### Switching to intel syntax
Option 1:
```c
asm(".intel_syntax noprefix\n"
	"code"
	".att_syntax\n"
);
```
Option 2:
Compile using the `-masm=intel` flag in gcc.
## Using nasm
Uses syntax very similar to intel.
One difference that it doesn't use the `PTR` keyword, usually it can be safely removed and it will function the same in nasm.
### Basic file structure (32 bit)
```assembly
section .data
    var1 db "Hello",0
    format db "%s", 0xd, 0xa,0 ; %s\n
section .text
global main
extern printf
main:
    push var1
    push format
    call printf
    add esp, 8 ; clean up the stack - 2 pushes of 4 bytes
    mov eax, 0 ; return value
    ret
```
### Creating executable
#### 64 bit
assembling: `nasm -f elf64 test.asm -o test.o`
linking: `gcc test.o -o test`
running: `./test`
#### 32 bit
assembling: `nasm -f elf32 test.asm -o test.o`
linking: `gcc -m32 test.o -o test`
running: `./test`