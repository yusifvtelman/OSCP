#Tool 
## Info

- **Type:** Web Directory/File Bruteforcing Tool
- **Common Usage:** Finding hidden files, directories, and endpoints on web servers
- **Supports:** GET requests, custom headers, multiple wordlists, and response filtering
- **Security Note:** Used during **web application enumeration** to discover sensitive or misconfigured files

## Basic Usage

### Basic Directory Bruteforce

```bash
dirsearch -u http://$IP -w /usr/share/wordlists/dirb/common.txt
```

- `-u`: URL of the target
- `-w`: Path to the wordlist

### Specific File Extension Bruteforce

```bash
dirsearch -u http://$IP -w /usr/share/wordlists/dirb/common.txt -x .php,.html
```

- `-x`: Specify file extensions to check (e.g., `.php`, `.html`)

### Using Custom Wordlist

```bash
dirsearch -u http://$IP -w /path/to/custom_wordlist.txt
```

### Restrict to Specific HTTP Status Codes

```bash
dirsearch -u http://$IP -w /usr/share/wordlists/dirb/common.txt --exclude-status 404
```

### Multi-threaded Scan

```bash
dirsearch -u http://$IP -w /usr/share/wordlists/dirb/common.txt -t 40
```

- `-t`: Number of threads for concurrent requests

### Exclude Certain Status Codes

```bash
dirsearch -u http://$IP -w /usr/share/wordlists/dirb/common.txt --exclude-status 404,403
```

- `--exclude-status`: Skip certain HTTP response codes (e.g., 404 for not found, 403 for forbidden)

## Notes

- **Usage:** Best used in the early stages of web application penetration testing for **directory and file discovery**.
- Useful for finding hidden **admin panels**, **config files**, **upload directories**, and **other sensitive files**.
- Supports **multi-threading** for faster enumeration.