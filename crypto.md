sudo hashcat -m 3200 '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm' /usr/share/wordlists/rockyou.txt  
sudo hashcat -m 3200 -a 0 -o found '$2y$10$0veO/JSFh4389Lluc4Xya.dfy2MF.bZhz0jVMw.V.d3p12kBtZutm' /usr/share/seclists/Passwords/Leaked-Databases/rockyou-75.txt 

https://unicornsec.com/home/tryhackme-crack-the-hash
hashcat -m 1800 '$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0' /usr/share/wordlists/rockyou.txt  

LTLM
hashcat -m 1000 -a 3 -w 3 a /usr/share/wordlists/rockyou.txt --show

hashcat hash /usr/share/wordlists/rockyou.txt -m 0 --force

/home/kali/tools/cracker/john/run/ssh2john.py id_rsa > id_rsa.hash

john id_rsa.hash --wordlist=/usr/share/wordlists/rockyou.txt