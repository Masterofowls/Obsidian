---
aliases: [sql, structured-query-language, database-query]
tags: [software, sql, database, query]
cssclass: wiki
---
# How SQL Works

## Overview
SQL (Structured Query Language) is used to **query and manipulate** data in relational databases.

## How It Works
1. User writes a SQL statement
2. **Parser** checks syntax and creates a query plan
3. **Optimizer** chooses the most efficient execution strategy
4. **Execution engine** runs the plan against the database
5. Results are returned as a table

## Basic Operations
```sql
SELECT name, age FROM users WHERE age > 25;
INSERT INTO users (name, age) VALUES ('Alice', 30);
UPDATE users SET age = 31 WHERE name = 'Alice';
DELETE FROM users WHERE name = 'Alice';
```

## How Indexes Speed Things Up
- Without index: scan every row (full table scan)
- With index: jump directly to matching rows (like a book index)
- B-tree is the most common index structure

## Related
- [[Wiki\Software\ORM|ORM]]
- [[Wiki\Security\SQL Injection|SQL Injection]]
