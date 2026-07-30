## Tips
- Go handles http request in parallel
- In Go, `=` means assign to an existing (global if declared in an outside scope) variable and `:=` means declare and assign. This means that a misuse of `=` can lead to a race condition if the same name is used in multiple places.
- Compile with the `race` flag to automatically detect race conditions.
- Loop variables are outer scope and overrided, applies when passed to functions by reference
- even in `a.b()`  `a` is passed by reference.
## CONNECT Trick
In a HTTP server, `CONNECT` requests aren't collapsed, supplying the path after the domain as-is, including trailing `/` and `..` and similar things.