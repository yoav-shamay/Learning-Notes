Allows to scan which ports are open on an ip address, and much more.
## GUI - zenmap
A GUI is available for usage, called zenmap
## Useful options
- **Always** use at least verbose level 2 `-vv`
- Aggressive mode `-A` activates service, OS, traceroute and common script scanning. is loud.
- `-p-` scan all ports (by default scans top 1000)
- `--top-ports <n>` - scan `n` most common ports (instead of 1000)
- timing control `-T <0-5>` controls speed and aggressiveness. higher number is faster. too high is loud and may be inaccurate. By default `3`
- `-O` get OS
- `-sV` get service version / type
- `--host-timeout 10s` - increase timeout if it answers too slow
- `-sC` - runs common scripts including basic vulnerability scan
## Scan Types
6 scan types.
Those are the most common:
`-sT` TCP connect scan
`-sS` SYN "half open" scan (default with sudo, preferred)
`-sU` UDP scan
Those are rarer, but usually stealthier than the top 3:
`-sN` TCP NULL scan
`-sF` FIN scan
`-sX` Xmas scan
### TCP connect scan
Checks if a port is open using 3 way handshake - sends SYN flag. If the response is RST flag, it is closed. if it's SYN+ACK, it's open.
After receiving SYN+ACK, sends ACK back to complete the handshake.
If it receives nothing, it's probably firewall protected (firewalls usually just drop incoming packets instead of returning that the connection is invalid. If it is configured to return a RST flag instead, it's hard to know).
### SYN scan
Instead of completing the handshake, sends RST flag after receiving SYN+ACK (the RST flag doesn't complete the handshake but prevents the server from repeatedly trying to make the request).
Referred also as "stealth" or "half-open".
Default when run with sudo permissions (-sT default without sudo)
PROS:
- Bypasses older IDS.
- It is usually not logged by the systems as the connection hasn't been established.
- It's faster as you don't have to complete and disconnect from the connection every time.
CONS:
- requires sudo permissions
- Sometimes brings down unstable clients
Generally better than TCP connect.
### UDP scan
When sending a UDP request to an open port, there should be no response. When it's closed, there should be an ICMP packet containing message indicating the port is unreachable.
So it sends a UDP request (twice to make sure) and if it receives no response it means the port is open or firewalled, so NMAP refers it as open|filtered.
Rarely there's a UDP response, in this case it will be referred as open.
When there's an ICMP response NMAP refers it as closed.
usually much slower, 20 minutes for 1000 ports.
Recommended to run with --top-ports number to run the number most commonly used UDP ports.
Usually sends empty UDP packets but in case for ports with common services sends protocol-specific payload that is more likely to bring a response.
### NULL, FIN and Xmas scan
NULL: Sends TCP request with no flags set.
FIN: Sends TCP request with only FIN flag.
Xmas: Sends malformed TCP.
Should be responded with RST if port is closed, otherwise no response (open or firewall).
Note that some servers send RST even in open ports, so won't work in this case. (Microsoft Windows and some Cisco networks)
Sometimes evades firewalls that filters SYN requests, but modern solutions still detect those scans.
## Ping Sweep
Sends ping to every ip address in a network. When it receives a response, it knows this address is alive.
Not always accurate.
Performed using the -sn flag With a range of ips, using hyphen or CIDR.
Examples:
`-sn 192.168.0.1-254`
`-sn 192.168.0.0/24`
The flag also causes to send TCP SYN to port 443 and TCP ACK (or SYN if not root) to port 80
## Scripts
Written in lua. There's a very extensive script library.
Those are some useful categories:
- `safe`: wont affect target
- `intrusive`: not safe, likely to affect target
- `vuln`: scan for vulnerabilities
- `exploit`: attempt to exploit a vulnerability
- `auth`: attempt authentication bypass for running services
- `brute`: attempt to brute force credentials for running services
- `query`: attempt to query running services for further information about the network
Full list: https://nmap.org/nsedoc/.
Run scripts:
- `--script=category` - run all applicable scripts in a category (only ones that target a detected running service)
- `--script=name1,name2,name3` - run the scripts called name1 or name2 or name3
- `--script-args 'a=b,c=d'` - give argument to a script
- `--script-help name` - a built-in help menu about a script
All scripts are saved in `/usr/share/nmap/script`.
`/usr/share/nmap/scripts/script.db` - file containing filenames and categories for every available script
download script:
`sudo wget -O /usr/share/nmap/scripts/<script-name>.nse https://svn.nmap.org/nmap/scripts/<script-name>.nse`
`nmap --script-updatedb`
## Firewall Evasion
- Stealth scans, NULL,FIN,XMAS try to evade firewalls blocking it
- Firewall usually blocks all pings, so an alive server will appear as dead. Using `-Pn` will tell nmap to not try to ping a machine before scanning, bypassing it,.
- `-f` - fragment the packets, making it less likely to be detected
- `--scan-delay timems` - adds delay, bypassing time-based firewalls
- `--badsum` - generates invalid checksums for packets. Real TCP/IP stack will drop those packets but a firewall might respond automatically, so allows to determine the existence of a firewall/IDS
- `--data-length <number>` - adds random data to packets, making them less suspicious
## Scanning for vulnerabilities
- Run with `-sV` to get service versions and search for matching vulnerabilities
- Run with **both** `-sV` and `--script=vuln` to do vulnerability scan
## Common ports and services
### Windows
- Port 445 - called `microsoft-ds` - actually [[SMB]]
### Linux
