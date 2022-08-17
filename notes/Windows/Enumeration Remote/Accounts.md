# Accounts
Brute force accounts / check accounts through Kerberos:
```bash
kerbrute userenum --dc <IP> -d '<DOMAIN>' <USERLIST> # --downgrade
```

Brute force accounts with RID through LSARPC pipe:
```bash
impacket-lookupsid '<DOMAIN>/<USER>:<PASS>@<IP>' # PTH

crackmapexec smb <IP> -u '<USER>' -p '<PASS>' --rid-brute # PTH

enum4linux-ng -u '<USER>' -p '<PASS>' -R -r 500-650,1000-1150 <IP>
```

All user accounts through SAMR pipe:
```bash
rpcclient -U '<USER>%<PASS>' <IP> -c 'enumdomusers' # PTH
rpcclient -U '<USER>%<PASS>' <IP> -c 'querydispinfo' # PTH
rpcclient -U '<USER>%<PASS>' <IP> -c 'queryuser <RID>' # PTH

impacket-samrdump '<DOMAIN>/<USER>:<PASS>@<IP>' # PTH
```

All user accounts through LDAP query:
```bash
impacket-GetADUsers -all -dc-ip <IP> '<DOMAIN>/<USER>:<PASS>' # PTH
```