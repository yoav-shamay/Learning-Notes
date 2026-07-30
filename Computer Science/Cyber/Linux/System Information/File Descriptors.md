Each open file has a number, a file descriptor.
Assigned sequentially - first open file is 3
By default:
0 - stdin
1 - stdout
2 - stderr
Linux functions like `open`, `read` and `write` use int to reference the file (`open` returns int, `read`, `write` get int) 