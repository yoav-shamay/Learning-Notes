A tool that allows analysing packet captures.
## Filtering
You can use the `and` or `or` words to combine multiple filters.
### By IP address
filtering by source ip: `ip.src==0.0.0.0`
by destination ip: `ip.dst=0.0.0.0`
### By protocol
Type the protocol name in order to filter packets only from this protocol, like `http` or `dns`
### Viewing field name
Right click the field in packet view and select `Apply as filter`.
It will show you how to filter by this field.
## Searching
Press Edit -> Find Packets
### By Text
Select `Packet Bytes` and `String`, and type the string you want to search.
## Exporting
You can export files using File -> Export Object, and selecting the protocol. 
Will automatically export the entire file even if it's split across multiple packets.
You need to Stop Capturing to do this.
You can also directly export a packet byte (including a single selected part, for example payload) using Right Click -> Export Packet Bytes
## Following packet stream
Using Analyze -> Follow
You can follow a packet stream, which means a specific communication and get all the data.
You can also try different numbers in the `udp.stream eq x` filter in order to view different streams
## Decrypting TLS
Edit -> Preferences -> Protocols -> TLS -> (Pre)-Master-Secret log filename
Set to path of ssl keylog file
## Statistics
Useful to find out-of-place packets, which might be suspicious.
Will only show based on filtered packets if a display filter is enabled.
### By Protocol
`Statistics -> Protocol Hierarchy`
### By Endpoints
`Statistics -> Endpoints`
## Troubleshooting
- If it doesn't seem to detect a protocol, make sure its enabled in Analyse -> Enabled Protocols