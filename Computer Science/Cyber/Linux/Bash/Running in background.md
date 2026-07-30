An ampersand (`&`) in the end of a command makes it run in the background.
Putting it in the end of a loop will make the entire loop run in background.
## Returning to foreground
You can use the `fg` command to return the process to foreground.
Just `fg` will return the latest job moved to background.
You can use `jobs` to see current jobs and use `fg %number` to return the job with number `number` back to foreground.