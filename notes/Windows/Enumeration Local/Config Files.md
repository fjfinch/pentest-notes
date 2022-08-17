# Config Files
##### Unattended installation
```bash
dir /b /s unattend.xml
dir /b /s sysprep.inf
dir /b /s sysprep.xml

C:\unattend.xml
%SystemRoot%\Panther\Unattend.xml
%SystemRoot%\Panther\Unattend\Unattend.xml
%SystemRoot%\system32\sysprep.inf
%SystemRoot%\system32\sysprep\sysprep.xml
```

##### Group Policy Preferences (GPP)
```bash
dir \\<HOST>\sysvol\groups.xml /b /s
dir \\<HOST>\sysvol\*.vbs /b /s
dir %AllUsersProfile%\Microsoft\Group Policy\groups.xml /b /s
dir %AllUsersProfile%\Microsoft\Group Policy\*.vbs /b /s

\\<HOST>\SYSVOL\<DOMAIN>\Policies\<FOLDER>\Preferences\Groups\Groups.xml
%AllUsersProfile%\Microsoft\Group Policy\History\<DOMAIN>\Machine\Preferences\Groups\Groups.xml

# Decrypt
gpp-decrypt <ENCRYPTION>
```

##### Third Party Software
```bash
# IIS web server
dir %SystemRoot%\Microsoft.NET\web.config /b /s

%SystemRoot%\Microsoft.NET\Framework64\v4.0.30319\Config\web.config
C:\inetpub\wwwroot\web.config

# McAfee
%AllUsersProfile%\Application Data\McAfee\Common Framework\SiteList.xml

# VNC
dir /b /s vnc.ini
reg query "HKLM\SOFTWARE\RealVNC\WinVNC4" /v password
```

```bash
reg query "HKLM" /f password /t REG_SZ /s
reg query "HKCU" /f password /t REG_SZ /s

# Windows Autologin
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon"
```