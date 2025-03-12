#Tool 
### Info

- **Type:** Network Scanner
- **Common Usage:** Host discovery, port scanning, service enumeration, OS detection, vulnerability detection
- **Supports:** TCP, UDP, OS detection, script scanning, version detection, output formats
- **Note:** One of the most essential tools during initial enumeration in penetration testing.

### Basic Scans

```bash
nmap $IP                      # Simple scan
nmap -sV $IP                  # Service/version detection
nmap -A -T4 $IP               # Aggressive scan (OS, script, traceroute)
nmap --top-ports 1000 $IP     # Top ports only
```

### Common Full Scan Template

```bash
nmap -sC -sV -T3 -oA initial_scan $IP
```

- `-sC`: Default scripts
- `-sV`: Version detection
- `-T3`: Balanced timing
- `-oA`: Save in all formats

### All TCP Ports

```bash
nmap -p- -T3 $IP
```

### Full Scan with Scripts

```bash
nmap -sC -sV -p- -T3 -oA full_scan $IP
```

### UDP Scan

```bash
nmap -sU -T4 $IP
```

### Specific Ports

```bash
nmap -p 21,22,80,443,3306 $IP
```

### Advanced Scans

```bash
nmap -O $IP                     # OS detection
nmap -sn 192.168.1.0/24         # Ping sweep
nmap 192.168.1.10-50            # IP range scan
```

### NSE Scripts

```bash
nmap --script vuln $IP
nmap --script smb-enum-shares -p445 $IP
nmap --script http-enum -p80 $IP
```

### Output Options

```bash
nmap -oN output.txt $IP     # Normal
nmap -oG output.gnmap $IP   # Grepable
nmap -oX output.xml $IP     # XML
```

### Firewall Evasion

```bash
nmap -f $IP                        # Fragment packets
nmap -sS -T1 $IP                   # Slow stealth scan
nmap --data-length 50 $IP          # Custom packet size
nmap --source-port 53 $IP          # Spoof source port
```

### Handy Flags

- `-Pn`: Skip host discovery
- `-n`: No DNS resolution
- `--open`: Show open ports only
- `--reason`: Show detection reason
- `--script-help=default`: List script details

