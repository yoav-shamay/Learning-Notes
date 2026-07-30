A windows debugging tool that can analyse crush dumps (`.dmp` files)
Can debug the processes at their crash.
## Obtaining .dmp file from memory dump
Can be done using [[memprocfs#Getting `dmp` format of process|memprocfs]] (preferred) or [[volatility2]] raw2dmp
## Selecting the process
Unnecessary if using process-specific dump, for example using `memprocfs`.
TODO write, see from https://www.sans.org/blog/analysis-user-data-vads-extraction-precise-data-notepad-memory-hunting-malware-behavior
## Viewing all heap allocated chunks
Run `!heap -s -v -a`.
It will list every allocated chunk in this format:
- Start address of the chunk (including metadata)
- Start address of user data
- Base address of the heap this chunk belongs to
- Base address of the heap segment this chunk belongs to
- Size of the chunk, including header
- Size of previous chunk
- Amount of unused bytes in the chunk
- Flags
TODO explanation about windows heap format and what does the extra flag mean, probably not here
## Inspecting memory
Run `db <address> L<length>`.