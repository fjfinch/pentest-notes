# Active Directory
Active Directory is the Windows implementation of a centralized general-purpose directory service, which uses LDAP as its primary protocol. Active Directory stores information about a variety of objects in the network such as user accounts, computer accounts, groups, and all related credential information used by Kerberos.

## Common protocols
|Service|port|Description|
|-|-|-|
|[[53 DNS\|DNS]]|53|Name resolution|
|[[88 Kerberos\|Kerberos, kpasswd]]|88,464|Authentication|
|[[135 RPC\|RPC, RPC over HTTP]]|135, 593|Communication|
|[[139,445 NetBIOS & SMB\|NetBIOS]]|137, 138, 139|Communication, name resolution|
|[[389 LDAP\|LDAP, tls]]|389, 636|Main directory service|
|[[139,445 NetBIOS & SMB\|SMB]]|445|Communication|
|Global catalog LDAP, tls|3268, 3269|-|

## AD Naming Conventions
Possible usernames can be calculated with username-anarchy:
`username-anarchy -i <NAMESLIST>`

firstlast
first.last
flast
f.last
firlas
fir.las
lastfirst
last.first
lastf
last.f

## Windows authentication
![KDC](auth.png)

Security Support Provider Interface (SSPI) is an API that allows connected applications to call one of several Security Support Providers (SSPs) to establish authenticated connections and to exchange data securely over those connections. It is equivalent to Generic Security Services (GSS)-API, and the two are on-the-wire compatible. SSP is the implementation of an authentication protocol as a dynamic link library (DLL).

SSPs:
* Negotiation
* Kerberos
* NTLM
* Secure Channel
* Digest
* CredSSP

To check if the credentials match they are checked against an account database. There are 2 account databases:
* Active Directory databaseL maintains the domain security principals.
* Security Account Manager (SAM) built-in database: maintains local security principals.

---

Windows uses multiple authentication suites/protocols. Most important are NTLM authentication (LM authentication, NTLMv1, NTLMv2 and NTLM2 Session) and kerberos authentication.

NTLM authentication is a family of authentication protocols that are encompassed in the Windows Msv1_0.dll. The NTLM authentication protocols include LM version 1 and 2, and NTLM version 1 and 2. The NTLM authentication protocols authenticate users and computers based on a challenge/response mechanism that proves to a server or domain controller that a user knows the password associated with an account.

Kerberos authentication is the preferred authentication method for Active Directory environments.

A Windows hash consists of 2 parts: LM:NT. NTLM and Kerberos all use the NT hash, also known as the Unicode hash. LM authentication uses the LM hash:
* LM hash: 2 parts DES. Stored for backward compatibility reasons. No longer need it
* NT hash: MD4 hash

#### Calculate NT hash
```Python
import hashlib,binascii
print(binascii.hexlify(hashlib.new('md4', "<PASSWORD>".encode('utf-16le')).digest()))
```