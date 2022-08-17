# Hashes
## Identify
```bash
name-that-hash -a -t <HASH>
hash-identifier <HASH>
hashid -em <HASH>
```

## Convert to hash
```bash
zip2john <ZIP> > <HASH> # use john
ssh2john <ID_RSA> > <HASH> # use john
```

## Crack
https://crackstation.net/

```bash
john --wordlist=<PASSLIST> --format=<HASHTYPE> <HASHFILE>
hashcat -m <MODE> <HASH> <PASSLIST> --potfile-disable -r /usr/share/hashcat/rules/<RULE>
```

|Service|port|
|-|-|
|MD5|0|
|SHA1|100|
|LM|3000|
|NTLM|1000|
|Pre-Auth 17|19800|
|Pre-Auth 18|19900|
|AS-REQ 23|7500|
|AS-REP 23|18200|
|TGS-REP 17|19600|
|TGS-REP 18|19700|
|TGS-REP 23|13100|