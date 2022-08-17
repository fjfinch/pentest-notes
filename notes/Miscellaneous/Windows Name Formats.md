# Windows Name Formats
Computer name:
* NetBIOS computer name
	* Computer account with $ sign
* DNS host name (device name)

Domain name:
* NetBIOS domain name
* DNS domain name

User account name:
* sAMAccountName
* user account name

---

userPrincipalName (UPN):
```bash
user account name@DNS domain name
```

Down-level logon name:
```bash
NetBIOS domain name\sAMAccountName
NetBIOS computer name\sAMAccountName
```