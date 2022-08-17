# Services on host
List all open ports/services:
```bash
# TCP
sudo nmap -sC -sV -p- <IP>

# UDP
sudo nmap -sU -sC -sV -p- <IP>
```