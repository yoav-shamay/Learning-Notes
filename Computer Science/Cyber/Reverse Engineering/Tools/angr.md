A library that allows for symbolic execution.
## Initialization
```python
import angr, claripy
project = angr.Project(FILE_NAME, auto_load_libs=False)
```
## Defining symbolic variable
```python
var = claripy.BVS("name", bit_length)
```
## Defining entry state
```python
state = project.factory.blank_state(addr=0x1234) # default - in the middle of logic or something, no additional setup
state = project.factory.entry_state() # real start of binary
state = project.factory.call_state(0x1234, arg1, arg2, arg3) # calling a function
```
### Additional options
To each one you can add a `add_options=[opt1,opt2]` for additional options
- `angr.options.ZERO_FILL_UNCONSTRAINED_MEMORY` - treat uninitialized memory as zero instead of symbolically.
- `angr.options.ZERO_FILL_UNCONSTRAINED_REGISTERS` - same for registers
## Configuring state
Can be done to entry state.
https://docs.angr.io/en/latest/core-concepts/states.html
Each value can either be set to a constant or to a symbolic variable
```python
state.regs.rbp = 0x1234
state.mem[0x1000].char = 0x56
state.mem[0x1000].uint64_t = 0x12345678
state.mem[0x100].uint64_t = symbolic_var
state.mem[0x100].uint64_t = symbolic_var.zero_extend(num_of_zeros_to_add) # useful if you know / assume a value is small, but you need to extend it to an entire integer
state.add_constraints(symbolic_var > 1000)
```
## Initializing simulation manager
```python
simgr = project.factory.simulation_manager(state)
```
## Defining goals
```python
simgr.explore(find=0x1234) # reach 0x1234
simgr.explore(find=[0x1234, 0x5678]) # reach one of 0x1234, 0x5678
simgr.explore(find=0x1234, avoid=0x5678) # reach 0x1234 without reaching 0x5678
simgr.explore(find=0x1234, avoid=[0x5678, 0x9abc]) # reach 0x1234 without reaching 0x5678 or 0x9abc

def is_valid(state):
	return state.mem[0x1234].uint32_t = 0x5678

def is_invalid(state):
	retrun state.mem[0x5678].char = 0x34
simgr.explore(find=is_valid,avoid=is_invalid)
```
Each of `find`, `avoid` can be a number (win/lose when reaching this), list (win/lose when reaching any of this) or a function (win/lose when this returns True)
## Getting solution
```python
if simgr.found:
	solution = simgr.found[0]
	solver = solution.solver
	# getting value of a symbolic variable
	value = solver.eval(symbolic_var)
else:
	print("No Solution Found")
	print(simgr.errored) # print errors that happebed
```
### Additional solver options
```python
# accessing constraints
constraints = solver.constraints
new_solver = claripy.Solver()
new_solver.add(constraints)
# adding additional constraints - note that it might be faster to add to state and reevaluate, should try both.
solver.add(symbolic_var < 1000000)
# getting min/max of variable - FOR THIS PARTICULAR PATH ONLY, AND NOT A CONTINOUS RANGE
min_val = solver.min(symbolic_var)
max_val = solver.max(symbolic_var)
# get up to n different solutions
solutions = solver.eval_upto(symbolic_var, max_sols)
```
## Getting many solutions
- `solutions = solver.eval_upto(symbolic_var, max_sols)` - gives them all at once, can be slow
This does it in a streaming manner and can be MUCH MUCH FASTER.
```python
for _ in range(100):
	# We add an inline constraint only for this specific 'eval'
	val = sol_state.solver.eval(var)	
	print(f"Found: {val}")
	# Now, forbid THIS specific value for the NEXT iteration
	sol_state.add_constraints(var != val)
	sol_state.simplify()
```
## Tips
- Try to simplify the logic for the solver, for example skipping parsing steps and placing the result directly in the memory. Try to use the solver only for the necessary logic, starting as late as possible and ending as early as possible.
- Running `solver.simplify()` after adding constraints 
## Troubleshooting
- printing `simgr.errored` can show errors that happened during the execution
- PIE base address is always `0x400000` even when IDA shows stuff with a bunch of 5