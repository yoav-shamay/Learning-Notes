## Accessing using gdb
TODO - how to run directly from gdb
And how to redirect stdio to fd and getting a pwntools tube for it
## Accessing using pwntools
```python
context.terminal = ["konsole", "-e"]

p = process("./exe")
_, debugger = gdb.attach(p, api=True)

p = gdb.debug(["./exe"], api=True)
debugger = p.gdb
```
## Methods
- `debugger.execute("cmd")` - execute command. does not guarantee waiting.
- `res = debugger.parse_and_eval("$rbp")` - evaluate an expression
- `debugger.wait()` - wait until reaching a breakpoint
- `debugger.continue_and_wait()` - equivalent to running continue and then wait
- 