Use `fickling path_to_pickle_file`, but returns in a weird format
pretty and good decompilation script:
```python
#!/usr/bin/env python3
#  usage:  python pickle2py.py  some.pkl  > recovered.py
import sys, tempfile, importlib.util as iu, subprocess, ast, textwrap, os
if len(sys.argv) != 2:
    sys.exit("usage: pickle2py.py pickle_file.pkl")

pkl = sys.argv[1]
dump_fd, dump_path = tempfile.mkstemp(suffix=".py")
os.close(dump_fd)
# 1) fickling dump
subprocess.run(["python", "-m", "fickling", pkl], check=True,
               stdout=open(dump_path, "w"))
# 2) patch __setstate__ once
if not hasattr(ast.AST, "__setstate__"):
    ast.AST.__setstate__ = lambda self, d: self.__dict__.update(d)
# 3) import dump, unparse AST
spec = iu.spec_from_file_location("dump", dump_path)
mod  = iu.module_from_spec(spec)
spec.loader.exec_module(mod)
tree = getattr(mod, "result0")
try:
    code = ast.unparse(tree)
except AttributeError:
    import astor; code = astor.to_source(tree)
print(textwrap.dedent(code))
os.unlink(dump_path)
```
save to a file called `pickle2py.py`, usage: `python3 pickle2py.py file.pickle > out.py`
TODO might be possible with fickling directly.