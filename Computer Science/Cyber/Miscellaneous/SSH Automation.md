Pwntools has a ssh class that allows automating ssh connections.
It allows to automatically run commands, and interact with local processes / remotes inside the ssh.
## Creating connection
```python
s = ssh(host="test", user="username", port=1111, password="guest")
```
## Interacting with local process / remote process
```python
r = s.remote("ip", port)
p = s.process(executable="path")
p = s.process(executable="path",argv=["a","b"])
```
## Running commands
```python
 out = s("echo hello")
 out = s["echo hello"]
 out = s.echo("hello")
 out = s.echo(["a", "b", "c"])
 out = s.system("echo hello | cat")
```