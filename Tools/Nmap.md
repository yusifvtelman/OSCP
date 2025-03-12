#Tool 
## Info

- **Type:** Network Scanner
- **Common Usage:** Host discovery, port scanning, service enumeration, OS detection, vulnerability detection
- **Supports:** TCP, UDP, OS detection, script scanning, version detection, output formats
- **Note:** One of the most essential tools during initial enumeration in penetration testing.

## Basic Commands

Basic Scan
```bash
nmap $IP
```

Aggressive Scan (with Scripts and Version Detection)
```bash
nmap -A -T4 $IP
```

Service & Version Detection
```bash
nmap -sV $IP
```

Top Ports Scan
```bash
nmap --top-ports 1000 $IP
```

Common Full Scan Template
```bash
nmap -sC -sV -T3 -oA initial_scan $IP
```

- `-sC`: Default scripts
- `-sV`: Service/version detection
- `-T3`: Timing (balanced)
- `-oA`: Output in all formats (normal, XML, grepable)

Full TCP Scan (All Ports)
```bash
nmap -p- -T3 $IP
```

Full Scan with Scripts and Versions
```bash
nmap -sC -sV -p- -T3 -oA full_scan $IP
```

UDP Scan
```bash
nmap -sU -T4 $IP
```

Specific Port Scan
```bash
nmap -p 80,443,3306 $IP
```

OS Detection
```bash
nmap -O $IP
```

Scan Specific Subnet or Range
```bash
nmap 192.168.1.0/24
nmap 192.168.1.10-50
```

Host Discovery Only (Ping Sweep)
```bash
nmap -sn 192.168.1.0/24
```

Script Scanning (NSE)
```bash
nmap --script vuln $IP
```

- Run default vulnerability scripts

```bash
nmap --script smb-enum-shares -p445 $IP
nmap --script http-enum -p80 $IP
```

Save Output
```bash
nmap -oN output.txt $IP          # Normal
nmap -oG output.gnmap $IP        # Grepable
nmap -oX output.xml $IP          # XML
```

Bypass Firewall / IDS
```bash
nmap -f $IP                         # Fragment packets
nmap -sS -T1 $IP                    # Stealthy slow scan
nmap --data-length 50 $IP          # Randomize packet size
nmap --source-port 53 $IP          # Spoof source port (e.g., DNS)
```

## Other Useful Options

- `-Pn`: Skip host discovery (assume host is up)
- `-n`: Skip DNS resolution
- `--reason`: Show why ports are detected as open/closed
- `--open`: Show only open ports
- `--script-help=default`: List available scripts
