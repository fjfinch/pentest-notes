# Services on host
List all open ports/services:
```bash
netstat -an | findstr "\[\:\:\] 0.0.0.0"
```

Find other IP addresses on network:
```bash
arp -a
```