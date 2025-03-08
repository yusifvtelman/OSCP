#Tool #AD
## Info

- **Type:** Active Directory (AD) Attack Tool
- **Common Usage:** BloodHound is used to map Active Directory (AD) attack paths and identify potential privilege escalation opportunities in an AD environment.
- **Security Note:** BloodHound helps in identifying attack paths that lead to domain admin rights and can be used during red team engagements to gain administrative access.

## Basic Usage
### BloodHound Enumeration

BloodHound uses the SharpHound tool to collect information about users, groups, permissions, trusts, and other AD objects.
```bash
SharpHound.exe -ip $IP -o json -c All
```

- `-ip $IP`: Specify the IP of the domain controller.
- `-o json`: Output the data in JSON format.
- `-c All`: Collect all information related to users, groups, trusts, and permissions.

### Importing Data into BloodHound

After gathering data with SharpHound, you can import the results into BloodHound for visualization.

```bash
bloodhound -i data.json
```

## BloodHound Commands
### BloodHound for Active Directory Enumeration
```bash
# Search for a User’s Group Memberships
bloodhound -ip $IP -u $USERNAME -group
```

```bash
# Finding Privilege Escalation Paths
bloodhound -ip $IP -u $USERNAME --find-paths
```

```bash
# BloodHound Enumeration
SharpHound.exe -ip $IP -o json -c All
```