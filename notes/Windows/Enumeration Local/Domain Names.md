# Domain Names
Check if host in joined to domain
```bash
systeminfo | findstr /B "Domain"
```

```bash
echo %USERDNSDOMAIN% # DNS domain name / unset
echo %USERDOMAIN% # NetBIOS domain name / NetBIOS host name

hostname # DNS host name
echo %COMPUTERNAME% # NetBIOS host name
echo %LOGONSERVER% # NetBIOS host name

net groups /domain #List of domain groups
net group "domain computers" /domain #List of PCs connected to the domain
net view /domain #Lis of PCs of the domain
nltest /dclist:<DOMAIN> #List domain controllers
net group "Domain Controllers" /domain #List PC accounts of domains controllers
net group "Domain Admins" /domain #List users with domain admin privileges
net localgroup administrators /domain #List users that belongs to the administrators group inside the domain (the group "Domain Admins" is included here)
net user /domain #List all users of the domain
net user <ACCOUNT_NAME> /domain #Get information about that user
net accounts /domain #Password and lockout policy
nltest /domain_trust #Mapping of the trust relationships.
```

```bash
USERDOMAIN=OPSEC # NetBIOS domain name / NetBIOS host name
USERDNSDOMAIN=OPSEC.TEST # DNS domain name / unset

COMPUTERNAME=OPSEC-DC01 # NetBIOS host name
LOGONSERVER=\\OPSEC-DC01 # NetBIOS host name
```