# other
Check if host is Windows or Linux:
```bash
ping <IP>
# TTL 128 - Windows
# TTL 64 - Linux/Unix
```

All useful LDAP objects through LDAP query:
```bash
ldapdomaindump -u '<DOMAIN>\<USER>' -p '<PASS>' --no-json --no-grep <DC_IP> # PTH
```

Enum password policy through SAMR pipe:
```bash
rpcclient -U '<USER>%<PASS>' <IP> -c 'getdompwinfo' # PTH
rpcclient -U '<USER>%<PASS>' <IP> -c 'getusrdompwinfo <RID>' # PTH

polenum -u '<USER>' -p '<PASS>' -d <IP>

crackmapexec smb <IP> -u '<USER>' -p '<PASS>' --pass-pol # PTH
```

Enum printers through SPOOLSS pipe:
```bash
rpcclient -U '<USER>%<PASS>' <IP> -c 'enumprinters' # PTH
```

# Bloodhound
```bash
# Ingestor
SharpHound.ps1 # for on-premise AD
AzureHound.ps1 # for Azure AD
python3 bloodhound.py -c All -d '<DOMAIN>' -ns <IP> -u '<USER>' -p '<PASS>'

# GUI
neo4j console # database
bloodhound
```