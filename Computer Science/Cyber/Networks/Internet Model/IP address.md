## Private Addresses
192.168.1.0 - network address
192.168.1.255 - broadcast address (all hosts in network)
Finding the address:
- windows: ipconfig
- linux: ifconfig or ip address show
Private IP address ranges:
 - 10.0.0.0 - 10.255.255.255 (10/8)
 - 172.16.0.0 - 172.31.255.255 (172.16/12)
 - 192.168.0.0 - 192.168.255.255 (192.168/16)
 Subnet mask: 255.255.255.0, or equivalently /24, means that the first 24 bits doesn't change in the network (subnet)
