## Bypassing Limitations
- In a domain, `a.com@b.com` usually parses `a.com` as the username and `b.com` as the actual domain, practically ignoring `a.com` in most cases, allowing to add any prefix you want to the url. for example `backend@127.0.0.1` is mostly equivalent to `127.0.0.1`. only happens if the `@` is before any `/` character.
- You can send a url through url shortener (tinyurl works, anything that sends 301) for url visiting to bypass character blacklist on the url, most http request libraries will automatically perform the redirected request.
- In a domain, `a.com\@b.com` gets often turned to `a.com/%5C@b.com` (or just treat the backslash as slash), so `a.com\@b.com/../` is practically equivalent to `a.com`, but in some parsers (including `urllib.parse.urlparse`), it will think of the hostname is `b.com`.
## Special Wrappers
- `file://path` might allow to read a file