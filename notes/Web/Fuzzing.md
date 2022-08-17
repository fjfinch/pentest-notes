# Fuzzing
```bash
gobuster dir -u <SCHEME>://<IP-FQDN>/ -w <WORDLIST> -x <EXTENSIONS> -e
fuff -u <IP-FQDN>/FUZZ -w <WORDLIST> -fs <FILTER_SIZE>
python3 dirsearch.py -u <SCHEME>://<IP-FQDN>/ -w <WORDLIST> -e <EXTENSIONS> -f -r
```
Extensions: html,php,asp,aspx,txt,js,css,ssh,sh