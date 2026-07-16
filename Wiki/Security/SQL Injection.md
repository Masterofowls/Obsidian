---
aliases: [sql-injection, sqli, injection-attack]
tags: [security, sql, injection, attack, database]
cssclass: wiki
---
# How SQL Injection Works

## Overview
SQL injection is an attack where malicious SQL code is inserted into input fields to **manipulate the database**.

## How It Works

### Normal Query
```sql
SELECT * FROM users WHERE name = 'John'
```

### Injected Query
User inputs: `' OR '1'='1`
```sql
SELECT * FROM users WHERE name = '' OR '1'='1'
```
This returns **all users** because `'1'='1'` is always true.

## Attack Types

### In-Band SQLi
- Results visible directly in the page
- **Error-based** — database errors reveal structure
- **Union-based** — combines results from injected query

### Blind SQLi
- No visible output
- **Boolean-based** — true/false responses
- **Time-based** — `WAITFOR DELAY '0:0:5'` causes delays

### Out-of-Band
- Data exfiltrated via DNS or HTTP requests

## Prevention
- **Parameterized queries** (prepared statements)
- **ORMs** — never write raw SQL with user input
- **Input validation** — sanitize and whitelist
- **Least privilege** — database user should have minimal permissions

## Related
- [[Wiki\Software\SQL|SQL]]
- [[Wiki\Software\ORM|ORM]]
