## Passing arguments
All parameters are pushed to the stack, the first parameter is at the lowest address, which means they are pushed in reverse order.
The first parameter is pushed at `ebp + 0x8` of the callee. Assuming its length is 4 bytes, the next one is on `ebp + 0xc` and so on.
The value of `ebp` is actually meaningless due to prologue.
You actually just place it after the function in the stack, one position after the return address.
Example in ROP:
```python
payload += p32(exe.plt["system"])
payload += p32(0) # next return address
payload += p32(binsh_addr)
```