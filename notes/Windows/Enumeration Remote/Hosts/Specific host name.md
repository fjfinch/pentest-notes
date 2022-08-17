## LDAP servers
All LDAP server names through SRV DNS record:
```bash
dig srv @<DNS_IP> '_ldap._tcp.<DOMAIN>'
```

LDAP server name through LDAP query:
```bash
ldapsearch -h <LDAP_IP> -x -s base ldapServiceName serverName
```

## Kerberos servers
All Kerberos server names through SRV DNS record:
```bash
dig srv @<DNS_IP> '_kerberos._tcp.<DOMAIN>'
```

## DNS servers
Kerberos server name through LDAP query:
```bash
ldapsearch -h <LDAP_IP> -x -s base dnsHostName
```