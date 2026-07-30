Different charsets can result in different characters for same bytes.
The browser chooses how to parse it based on the charset parameter in `Content-Type`
If it's different from the charset of the code validation, it can easily bypass blacklists.
The default for almost anything is UTF8.
If a charset is unsupported by browser, it will default to TODO
Example challenge: google ctf lost in transliteration