Slower but more reliable than UDP, verifies packets arrive.
# 3-Way Handshake
Browser -> Server: SYN
Server -> Browser: SYN/ACK
Browser -> Server: ACK
## Acknowledgements
After every request the server sends ACK to say the client shouldn't resend, even before a response. It's a simple small TCP response.