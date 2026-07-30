## Strategies
- Regex can be used for cheap filtering and substitutions on strings.
- You can convert most things to string using str and back using eval.
- Recursion in function (lambda or normal) can allow for potentially cheaper loops
## Shorter Alternatives
- `a | b` = `a or b`
- `a & b` = `a and b`
- You can encode a list of numbers as bitmask, and for example check `in` like this: `bm >> num & 1`
### Conditions
- `[a,b][cond]` = `b if cond else a`
- `a * cond` = `a if cond else 0`
- `a ** cond` = `a if cond else 1`