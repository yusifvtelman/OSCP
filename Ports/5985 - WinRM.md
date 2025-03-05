## Info
- **Type:** Remote Management Protocol
- **Common Usage:** Remote command execution, configuration management, and system administration tasks.
- **Security Note:** WinRM is typically unencrypted over HTTP (port 5985). It is recommended to use HTTPS (port 5986) to ensure encrypted communication and prevent MITM attacks.

## Basic Commands

```bash
# Connect to a remote system using evil-winrm
evil-winrm -i $IP -u $USER -p $PASSWORD
```

