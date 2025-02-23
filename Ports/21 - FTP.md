## Info
- **Type:** File Transfer Protocol
- **Common Usage:** Transferring files between a client and a server. Often used for website management and backups.
- **Security Note:** FTP transmits credentials in plaintext. Anonymous login or misconfigured access can expose sensitive files. Consider using SFTP or FTPS for secure alternatives.

## Basic Commands

```bash
# Connect to an FTP server
ftp $IP

# Login as anonymous (if allowed)
ftp $IP
Username: anonymous
Password: anonymous@domain.com

# List files on the remote server
ls

# Download a file from the server
get filename

# Upload a file to the server (if writable)
put filename

# Exit the FTP session
bye
```
