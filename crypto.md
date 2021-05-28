sudo hashcat -m 3200 '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm' /usr/share/wordlists/rockyou.txt  
sudo hashcat -m 3200 -a 0 -o found '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm' /usr/share/seclists/Passwords/Leaked-Databases/rockyou-75.txt 

https://unicornsec.com/home/tryhackme-crack-the-hash
hashcat -m 1800 '$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0' /usr/share/wordlists/rockyou.txt  

LTLM
hashcat -m 1000 -a 3 -w 3 a /usr/share/wordlists/rockyou.txt --show

hashcat hash /usr/share/wordlists/rockyou.txt -m 0 --force

/home/kali/tools/cracker/john/run/ssh2john.py id_rsa > id_rsa.hash

john id_rsa.hash --wordlist=/usr/share/wordlists/rockyou.txt



```
sunny@sunday:/backup$ cat shadow.backup
mysql:NP:::::::
openldap:*LK*:::::::
webservd:*LK*:::::::
postgres:NP:::::::
svctag:*LK*:6445::::::
nobody:*LK*:6445::::::
noaccess:*LK*:6445::::::
nobody4:*LK*:6445::::::
sammy:$5$Ebkn8jlK$i6SSPa0.u7Gd.0oJOT4T421N2OvsfXqAT1vCoYUOigB:6445::::::
sunny:$5$iRMbpnBv$Zh7s6D7ColnogCdiVE5Flz9vCZOMkUFxklRhhaShxv3:17636::::::

cat hash.txt
$5$iRMbpnBv$Zh7s6D7ColnogCdiVE5Flz9vCZOMkUFxklRhhaShxv3
hashcat -m 7400 hash.txt /usr/share/wordlists/rockyou.txt --force
```


```
 GetNPUsers.py -format john -no-pass -k -usersfile users -dc-ip 10.10.10.161 HTB.LOCAL/

john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt 

```
### Kerberos - 13100
```
root@kali:~# hashcat -a 0 -m 13100 tgs-administrator.hash /usr/share/wordlists/rockyou.txt –force
root@kali:~# hashcat -m 13100 tgs-administrator.hash –show
$krb5tgs$23$*Administrator$ACTIVE.HTB$active/CIFS~445*...[hash-value]...:Ticketmaster1968
```
