# Types of SQL Injection

## In-Band SQL Injection
This classic technique uses the same communication channel for sending payloads and receiving results.

### Error-Based
Attackers exploit database error messages printed on-screen to learn about the schema and extract data.

### Union-Based
Combines attacker queries using `UNION` to return additional data.
Example:
```sql
0 UNION SELECT 1,2,database();  
0 UNION SELECT 1,2,group_concat(table_name) FROM information_schema.tables;
```

---

## Blind SQL Injection
Occurs when the application does not display errors or data directly.

### Boolean-Based
The attacker infers results by sending true/false queries and observing application behavior.

Example:
```SQL
' OR '1'='1' --  
' AND substring(database(),1,1)='a' --
```

### Time-Based
The attacker uses commands like `SLEEP()` to measure response delays.

Example:
```sql
' OR IF(1=1, SLEEP(5), 0)--
```

A delay indicates a successful injection.

---

## Out-of-Band SQL Injection
This advanced technique uses two separate communication channels — one to inject, another to capture outbound data, often through DNS or HTTP requests to attacker-controlled servers.

---

See [[Burp Suite - Repeater]]for manual SQL injection testing workflow.
