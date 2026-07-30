## Docs
https://perldoc.perl.org/
## CGI Functions
### upload
Takes the file with the provided field name (in form data), uploads it to a temporary file (that will be removed when the script finishes), and returns a handle to it.
In case of multiple files with this name, uploads all of them and returns an array of handles.
Uses Perl temp file creation.
The directory is in the `TMPDIR` environment variable.
### param
Returns the parameter with the given name, from form data body. 
In case of multiple, returns the first one.
## Operators
### `<smth>`
Reads from the file handle `smth`.
If it's a string (or variable that contains a string), reads from the file handle variable named as the value of the string.
## File reading Vulnerability
Reading a file in Perl using `open` is vulnerable to arbitrary command injection.
To exploit: `; cat "/etc/passwd |"`. The `;` in the beginning is to ignore the prefix, can remove
The file handler will be to the stdout of the program,
## quote function sql injection
the `quote` function isn't secure if you can fully control the value, read https://stackoverflow.com/questions/40273267/is-perl-function-dbh-quote-still-secure (use 2 instead of NUMERIC for second value)
## Running a local server
For initial setup, see https://serverfault.com/questions/752272/run-perl-cgi-scripts-on-centos-7-with-apache-httpd
Use Apache server on wsl: `sudo systemctl start apache2`.
On arch: `sudo systemctl start httpd`
Access it in `localhost:1234`, can also from my computer.
Put perl script in `/var/www/perl`, or `/srv/http/perl` on arch.
Access at `localhost:1234/perl/name.cgi`
## CGI duplicate form data parameter
- When putting a form data parameter both as file and normal data, `upload` will still upload the file but further `param` calls will use the string provided.
- In this case, using `<$file>` will try to access the file handler whose name is the value of `$file`, and read from it.
- Can use with `ARGV` to control.
## ARGV list in CGI
Contains URL parameters (keys? values? - currently tested for valueless parameters).
Can fully control
## `<>` or `<ARGV>` or `<"ARGV">`
Reads each command line argument AS A NAME OF A FILE and reads it.
Can read arbitrary files by injecting command line arguments.
Can be used with [[#File reading Vulnerability]] to get full RCE.