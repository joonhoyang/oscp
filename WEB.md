## Please the scan for sub directory if seen dir

```
gobuster -u http://10.10.180.150:49663/ -w /usr/share/seclists/Discovery/Web-Content/common.txt -│ seconde -k -l -s "200,204,301,302,307,401,403" -x "txt,html,php,asp,aspx,jsp" -o "/home/kali/tools/enumeration/autorecon/results/10.10.180.150/scans/tcp_49663_h
gobuster dir -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -t 30  -u "http://10.10.217.69:49663" 
gobuster -u http://10.10.10.56/cgi-bin/ -w /usr/share/wordlists/dirb/common.txt -t 30 -x .php,.sh,.html
feroxbuster -u http://10.10.151.178 --wordlist /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt

wpscan --url https://brainfuck.htb --disable-tls-checks --enumerate p --enumerate t --enumerate u 
```

## PHP file upload script - drupal
```
https://vk9-sec.com/drupal-7-x-module-services-remote-code-execution/
```