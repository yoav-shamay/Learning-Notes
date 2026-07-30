## Site paths
- [[Gobuster]]
- `ffuf -u https://url/FUZZ -w wordlist.txt` 
## URL Parameters
`ffuf -u 'http://url/index.php?FUZZ=id' -ic -t 100 -w wordlist`

In addition, add a filter. Should expect something different. non empty response is `-fs 0`.
If you want something different do `-fs <normal size>` (with the other parameters set to normal situation). 
## HTTP Authorization
`sudo nmap -vv <site-addr> -p 80 --script=http-brute --script-args 'http-brute.path=<page-path>'`
## Wordlists
Assumes `seclists` is installed.
- Site paths - initial, including extensions - `/usr/share/seclists/Discovery/Web-Content/common.txt`
- Site paths without extensions (directories for example) - `/usr/share/dict/directory-list-2.3-small.txt` on arch (or `medium/large`)
- Bigger than `common.txt` - `/usr/share/seclists/Discovery/Web-Content/big.txt`
- url parameters - `/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt`