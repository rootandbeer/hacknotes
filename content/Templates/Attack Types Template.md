---
attack_type: "SQL Injection"
tools: [sqlmap, burpsuite]
tags: [attack/web/sql-injection]
date: 2024-12-15
---
# SQL Injection
**Definition**: Exploiting user input to execute SQL queries.

## Tools
- **Sqlmap**: Automates SQL injection detection and exploitation.
- **Burp Suite**: Intercept and inject payloads.

## Example Payloads

```sql
' OR 1=1 --
' UNION SELECT username, password FROM users --
```

## Steps

1. Identify injectable fields via `"` or `'`.
2. Use automated tools or manual payload crafting.