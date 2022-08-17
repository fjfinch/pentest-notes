## IP -> host name
Host names through PTR DNS record (reverse lookup):
```bash
dig @<DNS_IP> -x 127.0.0.1
dig @<DNS_IP> -x <IP>
```

Host name & other through SRVSVC & LSARPC over SMB & RPC:
```bash
nbtscan <IP>
nmblookup -A <IP>
```

## Host name -> IP
IP address of host through A DNS record:
```bash
dig a @<DNS_IP> '<HOST>'
```

Host name & other through SRVSVC & LSARPC over SMB & RPC:
```bash
nmblookup <HOST>
```