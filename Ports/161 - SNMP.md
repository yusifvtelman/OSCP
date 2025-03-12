## Info

- **Type:** Network Management Protocol (UDP)
- **Common Usage:** Monitoring and managing network devices (e.g., routers, switches, servers)
- **Security Note:** Often misconfigured with default community strings like `public` or `private`, which may allow full read access.

## Enumeration Tools & Usage

### `Snmpwalk` Command
```bash
snmpwalk -v2c -c public $IP
```

- `-v2c`: SNMP version 2c
- `-c`: Community string

```bash
# System information
snmpwalk -v2c -c public $IP 1.3.6.1.2.1.1.1

# Network interfaces
snmpwalk -v2c -c public $IP 1.3.6.1.2.1.2.2
```

### `Snmp-check` Command
```bash
snmp-check $IP -c public
```

- Gathers device info such as OS, users, processes, and network config.

### `Snmpenum` Command
```bash
snmpenum -t $IP -c public
```

- Extracts detailed SNMP information (users, groups, devices, etc.)

### `Onesixtyone` Command
```bash
onesixtyone -c wordlist.txt $IP
```
- Community String Bruteforce