#AD #Attack
## Info

- **Type:** Privilege Escalation / Active Directory Enumeration Attack
- **Common Usage:** Used to extract password hashes (NTLM, Kerberos) from the domain controller without needing to directly access the domain controller.
- **Used By:** Attackers with sufficient permissions (Domain Admin or Enterprise Admin) to impersonate a domain controller.
- **Security Note:** Can be used to **dump credentials** for offline cracking, leading to full compromise of user accounts, especially **Domain Admins**.

## Prerequisites

- **Required Permissions:** The attacker must have **Domain Admin** or **Enterprise Admin** privileges, or **Replication rights** on the target domain controller.
- **Tool:** **Mimikatz** is the most commonly used tool for performing the DCSync attack.

## Basic Usage

### Run DCSync Attack Using Mimikatz