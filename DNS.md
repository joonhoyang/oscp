
# with DNS - Should look for other URL  with DIG

```
nslookup
server 10.10.10.13
10.10.10.13

dig axfr friendzon.red @10.10.10.123
```
![image](https://user-images.githubusercontent.com/9059079/119153392-34f29e00-ba1f-11eb-9ee0-c47f113c8c72.png)

```
dnsrecon -t brt -d acmeitsupport.thm
```
