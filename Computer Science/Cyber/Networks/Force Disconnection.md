You can force a connection to disconnect, by sending invalid packets / disconnection packets on the name of the person you want to disconnect.
For example, you can send invalid TCP / TCP FIN / TCP RST packets.
This can make the client automatically reconnect, allowing you to sniff the reconnection.
This can be useful to extract credentials passed during authentication, if unencrypted or bruteforce-able.