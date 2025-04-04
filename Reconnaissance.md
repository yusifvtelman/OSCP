1. Port Scanning
2. Directory Scanning
## Port Scanning

### Tools
#### [[Nmap]]

```bash
nmap -sV -Pn -T4 $IP
```

```bash
nmap -T3 -sC -sV -oA initial_scan $IP
```

### Result
#### [[21 - FTP]]
#### [[22 - SSH]]
#### [[23 - Telnet]]
#### [[80 - HTTP]]
#### [[161 - SNMP]]
#### [[389 - LDAP]]
#### [[445 - SMB]]
#### [[873 - Rsync]]
#### [[1433 - MSSQL]]
#### [[1521 - OracleDB]]
#### [[3306 - MySQL]]
#### [[5432 - Postgresql]]
#### [[5985 - WinRM]]
#### [[6379 - Redis]]
#### [[27017 - MongoDB]]

## Directory Scanning
### Tools
#### [[Dirsearch]]
```bash
dirsearch -u $URL
```

#### [[Feroxbuster]]
```
```

#### [[Wfuzz]]
```bash
wfuzz -c -w /usr/share/wordlists/dirb/common.txt --hc 404 http://$IP/FUZZ
```
### Result
#### /[[DockerFile]]
#### /.[[Git]]
