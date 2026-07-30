## Easiest - with netcat
- `nc host port`
- `ncat host port`
## Alternative - without any required software
`(exec 3<>/dev/tcp/host/port; cat >&3; cat <&3; exec 3<&-)`
Replace `host` with host IP / name and `port` with the port.