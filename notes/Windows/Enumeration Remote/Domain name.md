# Domain name
Domain name & more:
```bash
# through LSARPC pipe:
rpcclient -U '<USER>%<PASS>' <IP> -c 'lsaquery' # PTH

# through SAMR pipe:
rpcclient -U '<USER>%<PASS>' <IP> -c 'lookupdomain <DOMAIN>' # PTH
rpcclient -U '<USER>%<PASS>' <IP> -c 'enumdomains' # PTH
rpcclient -U '<USER>%<PASS>' <IP> -c 'querydominfo' # PTH

# through LDAP query:
ldapsearch -h <IP> -x -s base namingContexts
```