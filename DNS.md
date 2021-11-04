
# with DNS - Should look for other URL  with DIG

```
nslookup
server 10.10.10.13
10.10.10.13

dig axfr friendzon.red @10.10.10.123
dig @10.10.10.161 htb.local dig @10.10.10.161 forest.htb.local

But it doesn’t let me do a zone transfer:
dig axfr @10.10.10.161 htb.local
```
![image](https://user-images.githubusercontent.com/9059079/119153392-34f29e00-ba1f-11eb-9ee0-c47f113c8c72.png)

```
dnsrecon -t brt -d acmeitsupport.thm
./sublist3r.py -d acmeitsupport.thm
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://MACHINE_IP
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://MACHINE_IP -fs {size}
./ffuf -c -w /usr/share/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.72.74/customers/signup -mr "username already exists"

```
```
user@machine$ ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host: FUZZ.acmeitsupport.thm" -u http://MACHINE_IP -fs {size}

```
