### nikto 
```
-id admin:PrettyAwesomePassword1234
```
### wordprocess - need to see plugins
```
wpscan --url http://10.10.10.88/webservices/wp -e ap --plugins-detection aggressive

```
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

Web Scanning:
#Web Scanning with extensions

Linux (Example web server might be Apache) gobuster dir -e -u http://10.10.10.10/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,js,txt,jsp,pl -s 200,204,301,302,307,403,401

Windows (Example web server might be IIS)

gobuster dir -e -u http://10.10.10.10/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,js,txt,asp,aspx,jsp,bak -s 200,204,301,302,307,403,401

Linux (Example web server might be Apache)

python3 dirsearch.py -r -u http://10.10.10.131/ -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -e php,html,js,txt,jsp,pl -t 50

Windows (Example web server might be IIS)

python3 dirsearch.py -r -u http://10.10.10.131/ -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -e php,html,js,txt,asp,aspx,jsp,bak -t 50

#HTTP gobuster dir -u http://10.10.10.10 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x php,html,txt -t 69

#HTTPS gobuster dir -k -u https://10.10.10.10/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t 69 (in some cases --wildcard will need to be used instead of -k)

#Nikto nikto -h 10.10.10.10 -p 80

#Nikto HTTPS ``nikto -h 10.10.10.10 -p 443```

WFuzz wfuzz -u http://10.10.10.10/hello.php?dir=../../../../../../../../../FUZZ%00 -w /usr/share/wfuzz/wordlist/general/common.txt

Web Shells
https://github.com/Arrexel/phpbash
https://github.com/flozz/p0wny-shell
