A suite of tools. Allows for capturing packets, cracking passwords and more.
## aircrack-ng
Allows cracking WEP key (old encryption method, weak) once enough encrypted packets were captured (using airodump-ng).
Uses the PTW method by default.
It also allows dictionary cracking (bruteforce with wordlist) of WPA / WPA2, with a captured four-way handshake as input (typically using airodump-ng), which allows for offline brute forcing of password.
## airodump-ng
Allows for capturing WiFi packets. Captures raw 802.11 frames.
Useful for collecting WEP / WPA Handshakes for aircrack-ng cracking.
In case you know the wifi password and have the capture handshake, you can decrypt the traffic (using airdecap-ng).
In case the WiFi has no password, the traffic is already unencrypted and you can read the original traffic.
## airdecap-ng
Allows to decrypt WEP/WPA/WPA2 capture files and strip wireless headers from unencrypted captures.

Gets either password or master key (not both).
If decrypting with password doesn't work (requires additional info) try with master key instead.
## airmon-ng
A convenience script that allows you to enable monitor mode your wireless interface.
Needed for example to capture traffic.
## aireplay-ng
Allows for injecting packets into the traffic, which allows for multiple attacks.
### Deauthentication
Sends disassociate packets to client, which makes it reconnect.
This can force them to reauthenticate and send the handshake again, which can be useful for capturing it, for aircrack-ng cracking or decrypting future traffic.