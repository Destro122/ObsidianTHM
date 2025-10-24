# SQL Injection Remediation

## Preventive Measures

### 1. Prepared Statements
Using parameterized queries separates data from code execution:
```php
$stmt = $pdo->prepare('SELECT * FROM users WHERE username = ?');  
$stmt->execute([$username]);
```
Prevents dynamic code alteration by treating input as data.

---

### 2. Input Validation
Restrict user input through:
- **Allow‑lists** (only expected input patterns).
- Rejecting special characters (`'`, `"`, `;`, `\`).

---

### 3. Escaping
Use escaping functions to neutralize special characters.  
Example in PHP: `mysqli_real_escape_string()` ensures dangerous sequences are interpreted as text.

---

## Developer Notes
Avoid using functions like `exec`, `system`, or unsafe concatenation in SQL statements.  
Regularly scan and audit applications for SQLi with web security tools.

---

