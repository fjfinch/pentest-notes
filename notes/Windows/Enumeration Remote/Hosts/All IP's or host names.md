## Both
All DNS records:
```bash
# through ANY DNS record:
dig any @<DNS_IP> '<DOMAIN>'

# through AXFR DNS record (zone transfer):
dig axfr @<DNS_IP> '<DOMAIN>'

# through LDAP query:
adidnsdump -u '<DOMAIN>\<USER>' -p '<PASS>' <DC_IP> # PTH
```

Host name & IP through SRVSVC & LSARPC over SMB & RPC:
```bash
nbtscan <IP>/<SUBNET>
```

## IP addresses
IP addresses on subnet:
```bash
sudo nmap -sn <IP>/<SUBNET>
```

## Host names
Subdomains through DNS brute force:
```bash
gobuster dns -d '<DOMAIN>' -r <DNS_IP> -w <WORDLIST>
```