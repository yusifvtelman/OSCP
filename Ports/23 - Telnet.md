## Info
- **Type:** Remote login protocol.
- **Common Usage:** Historically used for remote access and management of devices.
- **Security Note:** Telnet transmits all data, including credentials, in plaintext. This lack of encryption makes it highly insecure over untrusted networks. Misconfigured Telnet services can be exploited for unauthorized access.

## Basic Commands

```bash
# Connect to a Telnet service on a target IP
telnet $IP 23
```