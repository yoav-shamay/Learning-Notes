Reference
- www.gnu.org/software/bash/manual/bash.html#Shell-Operations
- https://www.gnu.org/software/bash/manual/bash.html#Executing-Commands
## Processing Order
1. The input is read from a file, argument or terminal
2. The input is broken into words and operators, separated by `metacharacters`. Alias expansion is performed in this step (see [[#Breaking into words (step 2)]])
3. The tokens are parsed into simple and compound commands.
4. Shell expansion is performed (see [[Bash Shell Expansions]])
5. Redirections are performed, and the redirections operators and operands are removed from the argument list (Note that redirections are detected in step 2, in this step they are performed)
6. The command is executed.
## Breaking into words (step 2)
This step obeys the quoting rules (words in quotes are kept, details in https://www.gnu.org/software/bash/manual/bash.html#Quoting)
TODO explain
## Parsing tokens (step 3)
TODO explain