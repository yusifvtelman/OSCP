#Database
## Info
- **Type:** Relational Database Management System (RDBMS)
- **Common Usage:** Used for storing and managing structured data for web applications, enterprise systems, and more.
- **Security Note:** Misconfigured MySQL servers might allow unauthorized access. Always verify credentials and consider testing for weak or default passwords.

## Basic Commands

```bash
# Connect to the MySQL server (you will be prompted for a password)
mysql -h $IP -u $USER -p

# Once connected, list all databases:
SHOW DATABASES;

# Switch to a specific database:
USE $DATABASE;

# List all tables in the selected database:
SHOW TABLES;

# Describe the structure of a specific table:
DESCRIBE $TABLE;
```

