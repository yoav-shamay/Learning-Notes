Syntax: `gobuster dir --url <url> --wordlist <wordlist>`
## Options
- `-k` - disable SSL validity check
- `-a "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0 Safari/537.36"` - fake user agent (might be worth doing)
- `-b <status codes>` - bad status codes (exclude)
- `-s <status codes>` - positive status codes (include)