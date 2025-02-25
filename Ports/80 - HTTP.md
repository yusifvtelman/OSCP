## Info
- **Type:** Hypertext Transfer Protocol (HTTP)
- **Common Usage:** Web services, websites, and API endpoints.
- **Security Note:** HTTP traffic is unencrypted. If credentials or sensitive data are transmitted over HTTP, they can be intercepted. Web applications may have vulnerabilities such as **SQL Injection (SQLi), Cross-Site Scripting (XSS), or misconfigured directories**.

## Basic Commands
### Enumerating Web Directories
```bash
# Dirsearch
dirsearch -u http://$IP

# Gobuster
gobuster dir -u http://$IP -w /usr/share/wordlists/dirb/common.txt -x php,html,txt
```

### Enumerating Web Subdomains
```bash
# Subdomain scan using Gobuster
gobuster dns -d target.com -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

### Checking Web Server Info & Headers
```
curl -I http://$IP
```

### Crawling the Website for Hidden Links
```bash
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://$IP
```

## Exploitation
### [[SQL Injection]] Testing 
### [[Cross-Site Scripting]] Testing
### [[File Upload]] Testing