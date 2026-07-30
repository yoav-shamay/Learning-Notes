- A good option is to patch the binary to bypass the anti-debugging check, or skipping it during debugging.
- Note that debugging (sometimes) puts breakpoint instruction instead of the byte in the location of the breakpoint, which can trigger a difference if the file reads its own code.
## Detecting anti debugging
- On linux - `/proc/self/status` read, search for `tracerpid` or similar.
- 