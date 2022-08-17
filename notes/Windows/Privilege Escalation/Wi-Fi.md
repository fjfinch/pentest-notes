# Wi-Fi
what for password? not domain?
```bash
netsh wlan show profile
netsh wlan show profile name="<NAME>" key=clear | findstr Key
```