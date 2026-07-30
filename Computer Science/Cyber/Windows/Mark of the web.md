A windows security protocol, implemented in most browsers.
When downloading files from the internet or other unsafe sources, windows saves metadata in an [[Alternate Data Streams|Alternate Data Stream]] called `Zone.Identifier`
If this data is present, windows will warn the user before running the file.
This metadata typically looks like this:
```
[ZoneTransfer]  
ZoneId=3  
ReferrerUrl=https://example.com/page  
HostUrl=https://example.com/file.exe
```
## ZoneId
Indicates where the file came from.
One of the following:
- `0` - local machine
- `1` - local intranet
- `2` - trusted sites
- `3` - internet (most common)
- `4` - restricted sites
## HostUrl
The URL the file was downloaded from
## ReferrerUrl
The page that linked to this download