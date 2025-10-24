## Common Scenario
Login forms often rely on SQL queries like:
```sql
SELECT * FROM users WHERE username='%user%' AND password='%pass%';
```

If the input is not sanitized, attackers can manipulate the query.

Example:
```sql
Username: ''  
Password: ' OR 1=1;--
```

Resulting query:
```sql
SELECT * FROM users WHERE username='' AND password='' OR 1=1;
```
The condition `1=1` is always true, granting unauthorized access.

---
## Practical Use
Bypassing authentication often leads to administrative or sensitive account access. Once in, SQLi can be chained with privilege escalation or remote code execution attacks.

---

