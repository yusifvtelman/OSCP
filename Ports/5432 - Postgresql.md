## Info
- **Type:** Relational Database Management System (RDBMS)
- **Common Usage:** Often used for web applications, data analysis, and as a backend for APIs.
- **Security Note:** PostgreSQL often runs with weak or default authentication settings, especially on test or development environments. It’s important to check for default credentials, misconfigurations, or accessible administrative features.

## Basic Commands
```bash
# Connect to PostgreSQL (prompt for password)
psql -h $IP -U $USER -d $DB_NAME

# List databases
\l

# Connect to a specific database
\c $DB_NAME

# List tables in the current database
\dt

# Describe the structure of a table
\d $TABLE_NAME

```