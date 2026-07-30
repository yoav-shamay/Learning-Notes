## 1. Physical Layer
How to physically transfer the data. For example: definition of 0,1 and the medium.
## 2. Data Link Layer
Transferring the data between components on the same network (LAN)
Info on how to communicate, detection/correction of some bit errors caused by physical layer.
Contains MAC addresses of source and destination.
Adds header and trailer, creating a frame.
It's usually split to LLC and MAC.
Examples of protocols: Ethernet (802.3), WiFi (802.11)
## 3. Network Layer
Responsible for the data transfer between different networks.
Includes routing and logical addressing (ip address).
Examples of protocols: IP, ICMP, IPsec, SSL/TLS VPN
## 4. Transport Layer
Responsible for communication between running applications on the hosts.
Ensures complete data transfer, error recovery and flow control between the hosts.
Segments and reassembles the data. Also has error detection and correction.
Also has multiplexing (combining multiple signals to one)
Examples of protocols: TCP, UDP
## 5. Session Layer
Responsible for establishing, maintaining and closing a session, and synchronizing the data (ensuring order and recovery mechanisms in case of data loss)
Examples: NFS, RPC
## 6. Presentation Layer
Responsible for the encoding/encryption/compression of the data.
It is the file format of the content.
Also has encryption and compression protocols.
For example: ASCII, Unicode, MIME, JPEG, PNG, MPEG
## 7. Application Layer
Responsible for the data related to the application itself, data used by the application.
Examples: HTTP, FTP, DNS, POP3, SMTP, IMAP
## TCP-IP Model
An implementation of the 7-layer model
layers 5-7 are grouped together in the application layer
Layer 3 (Network Layer) is called the Internet Layer
Layer 2 (Data Link Layer) is called the Link Layer

Packet order:
- Ethernet/Wifi Header
- IP Header
- TCP/UDP Header (called TCP segment / UDP datagram)
- Application Data
- Ethernet/Wifi Trailer
