#Tool 
## Info

- **Type:** Web Fuzzing Tool
- **Common Usage:** Fuzzing parameters, directories, files, headers, authentication points
- **Supports:** GET/POST requests, custom headers, multiple payloads, wordlists, response filtering

## Basic Usage

### Directory/Resource Fuzzing

```bash
wfuzz -c -w /usr/share/wordlists/dirb/common.txt --hc 404 http://$IP/FUZZ
```

- `-c`: Color output
- `-w`: Wordlist
- `--hc 404`: Hide responses with HTTP status code 404

### File Extension Fuzzing

```bash
wfuzz -c -w /usr/share/wordlists/dirb/common.txt -u http://$IP/FUZZ.php
```

### Virtual Host Fuzzing

```bash
wfuzz -c -w vhosts.txt -H "Host: FUZZ.$DOMAIN" http://$IP
```

### Parameter Fuzzing (GET)

```bash
wfuzz -c -w wordlist.txt -u "http://$IP/index.php?FUZZ=test"
```

### Parameter Fuzzing (POST)

```bash
wfuzz -c -w wordlist.txt -u "http://$IP/login.php" --hc 200 -d "user=FUZZ&pass=admin"
```

### Header Fuzzing (User-Agent, Referer, etc.)

```bash
wfuzz -c -w wordlist.txt -u http://$IP -H "User-Agent: FUZZ"
```

### Multiple Payloads (Multiple FUZZ markers)

```bash
wfuzz -c -w users.txt -w passwords.txt -u http://$IP/login.php?user=FUZZ&pass=FUZ2Z
```

## Filters

- `--hc`: Hide status code (e.g., 404, 403)
- `--hl`: Hide by response length
- `--hh`: Hide by response content
- `--hw`: Hide by number of words in response

## Notes

- Useful for **finding hidden files, admin panels, vhosts, parameters, weak auth mechanisms**
- Supports **Burp-style wordlists** and **custom encodings**
- Can be used in place of or alongside tools like `ffuf`, `dirsearch`, `gobuster`
