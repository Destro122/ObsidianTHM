## Overview
**SQL Injection (SQLi)** is one of the oldest and most damaging web vulnerabilities. It occurs when a web application uses unvalidated user input to construct database queries. Attackers can exploit this flaw to:
- Steal, delete, or alter data.
- Bypass authentication mechanisms.
- Execute arbitrary SQL commands on the database server.

SQLi targets relational databases such as MySQL, PostgreSQL, and Microsoft SQL Server.

---

## Databases and DBMS

A **database** stores structured collections of data, managed by a **Database Management System (DBMS)**.  
Two models exist:

- **Relational:** Data organized in tables (rows and columns) using SQL.  
  Examples: MySQL, PostgreSQL, SQLite.
- **Non‑relational (NoSQL):** Data stored in non-tabular structures such as documents or key‑value pairs.  
  Examples: MongoDB, Cassandra, Elasticsearch.

---

## Tables and Data Structure

Databases store data as:
- **Columns (fields):** Define data type (e.g., integer, string, date).  
- **Rows (records):** Contain individual data entries.

Each table often includes a **primary key** that uniquely identifies each row. Relationships between tables are handled through shared keys — the relational model.

---

## Core SQL Operations
The following SQL statements are most commonly used:

| Command | Description |
|----------|-------------|
| `SELECT` | Retrieve data from a table. |
| `INSERT` | Add new rows of data. |
| `UPDATE` | Modify existing data entries. |
| `DELETE` | Remove one or more rows. |

### Example Queries
```SQL
SELECT * FROM users;  
INSERT INTO users (username,password) VALUES ('bob','password123');  
UPDATE users SET password='root123' WHERE username='admin';  
DELETE FROM users WHERE username='martin';
```

---

## UNION
The `UNION` statement merges the results of two `SELECT` queries as long as both return the same number and type of columns. Attackers often use this feature to extract data across multiple tables.

---

## Query Filtering
The `WHERE` clause applies conditions:
```sql
SELECT * FROM users WHERE username='admin';  
SELECT * FROM users WHERE username LIKE 'a%';
```

---

