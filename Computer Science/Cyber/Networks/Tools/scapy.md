Python library that manages packets.
Allows sniffing, sending and reading pcap files.
## Imports
```python
from scapy.all import *
from scapy.layers.inet import * # for protocols like IP,TCP,UDP
from scapy.layers.http import * # for HTTP
```
## Sniff packets
```python
from scapy.all import *
capture = sniff(count=packet_count,[lfilter=filter])
for packet in capture:
	pass
```
## Filter
```python
def filter(packet):
	return IP in packet
```
## Get packet data
```python
print(packet[IP].src)
print(packet[TCP].sport) # source port
print(packet[Raw].load) # payload data
packet.show() # print general information about the packet
```
## Creating packets
```python
packet = IP() / UDP() / Raw()
packet[IP].dst = "127.0.0.1"
packet[UDP].dport = 80
packet[Raw].load = b"hello"
send(packet)
resp = sr1(packet) # send and recieve response
```
## Reading pcap files
```python
pcap = sniff(offline="traffic.pcap", session=TCPSession) # prefered - combines tcp sessions
pcap = rdpcap('capture.pcapng') # reads it as raw - treating as tcp packet as separate
for packet in pcap:
	packet.show()
```
## Layer data
### HTTP
There are 2 objects: `HTTPRequest` and `HTTPResponse`
#### HTTPRequest
```python
h = packet[HTTPRequest]
method = h.Method # http method - for example b'GET'
path = h.Path # request path - for example b'/register'
body = packet[Raw].load # http body
```