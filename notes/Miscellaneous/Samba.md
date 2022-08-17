# Samba
`sudo apt install samba`

### Create share
`mkdir /home/<USER>/<SHARE>/`

### Restart/check Samba
`sudo systemctl restart smbd.service`
`testparm`

### Add user for Samba auth
`sudo smbpasswd -a username`

### If firewall problems
`sudo ufw allow samba`

### Change config
`nano /etc/samba/smb.conf`

```
[<SHARE>]
    comment = Samba on Ubuntu
    path = /home/<USER>/<SHARE>/
```

#### Default
browsable = yes

#### stops null session
restrict anonymous = 2