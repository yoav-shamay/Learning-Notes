A type of race condition.
You quickly modify the DNS resolve of a url between 2 options with low TTL.
## Applications
- TOCTOU  if you check the resolved IP for whitelist / blacklist and then perform the request.
- Allows one URL to resolve for different websites in different occasions, including client side scripts, while being the same domain.
## Performing
- https://lock.cmpxchg8b.com/rebinder.html (untested) - will automatically swap the DNS between 2 IP's
### Custom DNS Server
You can program a custom DNS server to get more options (like CNAME - will resolve to another URL instead of IP).
Make sure to set a low TTL.
In order to make my code be the actual DNS resolver of some domain.
It can be done by running it on a public VM (see [[Free Server Hosting]]), and setting it as the NS of a subdomain (use freedns.afraid.org, see [[Custom DNS]])