Actually used for theorems, definitions
Should have a declaration in header and use in body.
## `\newtheorem` in header
Syntax:
- `\newtheorem{envname}{text}[parent counter]` - number will be a child of the parent counter, will appear as the parent counter dot the number inside the current parent section. example options: `section`, `subsection`.
- `\newtheorem{envname}[sharedcounter]{text}` - will share the same counter as `sharedcounter`, which can be the `envname` of previously declared `\newtheorem`
`envname` - identifier in the body
`text` - text that appears in document
Example:
```latex
\newtheorem{theorem}{Theorem}[section] % Theorem 1.2
\newtheorem{definition}{Definition}[subsection] % Definition 1.2.3
```
## In body
```latex
\begin{envname}
content
\end{envname}
```
Where `envname` is the name specified in the `\newtheorem`.
You can specify theorem name like this:
`\begin{envname}(theoremname)`