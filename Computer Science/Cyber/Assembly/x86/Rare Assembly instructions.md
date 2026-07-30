Using AT&T Syntax.
- `xlat ds:(rbx)` changes `al` to memory at address `rbx + al`
- `bextr rdx,rcx,rbx` - rdx is template, rcx is input and rbx is output. let's say `rbx = 0xabcd`, then `0xab` bits are taken starting from bit `0xcd` (from the lower ones), equivalent to `rbx = (rdx >> 0xcd) & ((1 << 0xab) - 1)`
- 