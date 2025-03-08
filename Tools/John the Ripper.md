#Tool 
## Info

- **Type:** Password Cracking Tool
- **Common Usage:** Cracking password hashes to recover plaintext passwords.
- **Security Note:** Often used during penetration tests to identify weak passwords and assess password strength.
- **Supported Hash Types:** Includes Unix crypt(3), Kerberos AFS, Windows LM, MD5, and others.

## Basic Commands

```bash
john --wordlist=$WORDLIST --format=$HASH_TYPE $HASH_FILE
```

- `--wordlist=$WORDLIST`: Specifies the wordlist file containing potential passwords.
- `--format=$HASH_TYPE`: Specifies the hash type (e.g., `md5`, `sha256`, `des`).
- `$HASH_FILE`: The file containing the password hashes to crack.
