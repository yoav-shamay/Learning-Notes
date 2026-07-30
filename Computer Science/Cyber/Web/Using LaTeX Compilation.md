## Reading file
`\input{file_name}` - will parse as latex (but might be able to see content in error)
## Command injection
https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/LaTeX%20Injection (untested)
## Bypassing limitations
- `\command{abc}` can be replaced with `\csname command\endcsname{abc}`
- This can be further substituted with:
```latex
\def\prefix{com}
\csname \prefix mand\endcsname{abc}
```