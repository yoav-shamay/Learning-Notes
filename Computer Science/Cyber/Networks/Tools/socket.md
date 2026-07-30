## TCP
### Client
```python
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))
msg = client_socket.recv(1024)
client_socket.send(b"abc")
client_socket.close()
```
### Server
```python
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((HOST, PORT))
server_socket.listen()
conn, address = server_socket.accept()
msg = conn.recv(1024)
conn.send(b"abc")
conn.close()
```
## UDP

### Client
```python
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
client_socket.connect((host, port))
msg = client_socket.recv(1024)
client_socket.send(b"abc")
client_socket.close()
```
### Server
```python
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_socket.bind((HOST, PORT))
msg, address = server_socket.recvfrom(1024)
server_socket.sendto(b"abc", address)
server_socket.close()
```