When a program leaves a file pointer open, it can be exploited in some cases.
## Dropping permissions
The permissions are only checked when opening the file, which means dropping the permissions won't prevent reading from this file descriptor.
In case a file pointer is unclosed, you can read from it using `<&number`
## Accessing file without full name
See [[proc Filesystem#`fd` Directory]] - if you have the file descriptor (can brute force) you can access the file.