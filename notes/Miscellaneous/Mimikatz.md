# Mimikatz
The primary command components are sekurlsa, kerberos and lsadump. Mimikatz requires administrator or SYSTEM (`token::elevate`) and often debug rights (`privilege::debug`) in order to perform certain actions. 

Starting with Windows 8.1 and Windows Server 2012 R2, the LM hash and “clear-text” password are no longer in memory. In order to prevent the “clear-text” password from being placed in LSASS, the following registry key needs to be set to “0” (Digest Disabled):
> HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest “UseLogonCredential”(DWORD)

## sekurlsa
After a user logs on, a variety of credentials are generated and stored in the Local Security Authority Subsystem Service, LSASS, process in memory. sekurlsa module interacts with the LSASS process in memory to gather credential data and provides enhanced capability over kerberos. Requirements: Administrator or a SYSTEM account.
* `sekurlsa::msv` - Lists LM & NTLM credentials
* `sekurlsa::ekeys` - List Kerberos Encryption Keys
* `sekurlsa::kerberos` - List Kerberos credentials for all authenticated users (including services and computer account)
* `sekurlsa::krbtgt` - Get Domain Kerberos service account (KRBTGT) password data
* `sekurlsa::logonPasswords` - Lists all available providers credentials. This shows recently logged on user and computer credentials
* `sekurlsa::tickets` - List Kerberos tickets of all sessions. Unlike kerberos::list, sekurlsa uses memory reading and is not subject to key export restrictions. sekurlsa can access tickets of others sessions (users). (export with `/export`)
* `sekurlsa::pth` - Pass-the-hash
* `sekurlsa::process` - Switch (or reinit) to LSASS process context
* `sekurlsa::minidump` - Switch (or reinit) to LSASS minidump context
* `sekurlsa::bootkey` - Set the SecureKernel Boot Key to attempt to decrypt LSA Isolated credentials
* `sekurlsa::credman` - 
* `sekurlsa::wdigest` - 

## kerberos
Kerberos module enables modification of Kerberos tickets and interacts with the official Microsoft Kerberos API. No special privileges required.
* `kerberos::list` - List (TGT and TGS) kerberos tickets of current user (export with `/export`)
* `kerberos::tgt` - Displays information about the TGT of the current session
* `kerberos::ptt` - Pass-the-ticket. Injects kerberos tickets (TGT or TGS) in the current session. If used with tickets external to mimikatz, tickets must be in Kerberos credential format (KRB_CRED)
* `kerberos::golden` - golden & silver tickets. Create a TGT or a TGS with arbitrary data, for any user you want, in groups you want
* `kerberos::purge` - Purges all tickets of the current session. Run this command before passing tickets (PTC, PTT, etc) to ensure the correct user context is used.

## lsadump
lsadump module enables dumping credential data from the Security Account Manager (SAM) database which contains the NTLM (sometimes LM hash) and supports online and offline mode as well as dumping credential data from the LSASS process in memory. Lsadump can also be used to dump cached credentials.
* `lsadump::sam` - Dumps the Security Account Managers (SAM) database. It contains NTLM, and sometimes LM hash, of local users passwords. It can work in two modes: online (with SYSTEM user or token) or offline (with SYSTEM & SAM hives or backup). Need SYSTEM privilege use: `token::elevate` if you're admin
* `lsadump::lsa` - Ask LSA Server to retrieve SAM/AD entries (normal, patch on the fly or inject). Use to dump all Active Directory domain credentials
* `lsadump::dcsync /user:<USER>` - Ask a DC to synchronize an object (get password data for account). No need to run code on DC
* `lsadump::trust` - Ask LSA Server to retrieve Trust Auth Information (normal or patch on the fly)
* `lsadump::secrets` - SECRETS entries
* `lsadump::cache` - MSCache
* `lsadump::backupkeys` - 
* `lsadump::rpdata` - 
* `lsadump::setntlm` - Ask a server to set a new password/ntlm for one user
* `lsadump::changentlm` - Ask a server to set a new password/ntlm for one user
* `lsadump::netsync` - Ask a DC to send current and previous NTLM hash of DC/SRV/WKS