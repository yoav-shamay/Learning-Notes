Can work on a lot of older machines, very recent.
## Exploit
Best exploit I found: https://github.com/SeanRickerd/cve-2026-31431/blob/main/exploit.py
Switch `/usr/bin/su` to any setuid binary if necessary (prob `/bin/su`).
Gives a shell immediately.