Check if host is Windows or Linux:
```bash
ping <IP>
# TTL 128 - Windows
# TTL 64 - Linux/Unix
```

All open ports:
```bash
# TCP
sudo nmap -sC -sV -p- <IP>

# UDP
sudo nmap -sU -sC -sV -p- <IP>
```

IP addresses on subnet:
```bash
sudo nmap -sn <IP>/<SUBNET>
```