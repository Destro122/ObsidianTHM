## Overview
**Burp Suite Intruder** is an automated fuzzing and brute-forcing tool designed to modify and resend requests with varying inputs.  
It allows penetration testers to:
- Perform brute-force attacks on login forms.
- Enumerate directories and virtual hosts.
- Fuzz parameters for vulnerabilities such as [[SQLi - Types]] or [[Command Injection]].

While Intruder is available in the Community Edition, it is **rate-limited** — meaning attacks proceed significantly slower than in Burp Professional. Despite this, Intruder is invaluable for learning request manipulation and payload placement.

Comparable tools include **Wfuzz** and **ffuf**.

---

## Interface Overview

### Positions Tab
When a request is sent to Intruder (Ctrl + I or “Send to Intruder”), the target field populates automatically.  
The **Positions** tab lets you mark parts of the request for payload insertion.  
Marked positions are enclosed in section symbols (§).

Key controls:
- **Add §** — Manually create payload positions.
- **Clear §** — Remove all selected positions.
- **Auto §** — Burp automatically identifies common insertion points.
Example:
```
username=§admin§&password=§1234§
```
---

### Payloads Tab
Defines which input values will be inserted into the marked positions.  
You can add payloads manually or load them from a wordlist.

#### Sections:
- **Payload Sets** – Assign specific payloads to particular positions.
- **Payload Settings** – Manage content (load, remove, clear).
- **Payload Processing** – Apply transformations like capitalization, regex filtering, or skipping invalid entries.
- **Payload Encoding** – Adjust encoding for characters (default: URL encoding).

---

### Resource Pool & Settings Tabs
- **Resource Pool** — Handles resource allocation (useful only in Burp Pro).  
- **Settings** — Configure attack behavior, define highlight filters (e.g., “Show only responses with HTTP 200”), and flag patterns in responses.

---

## Attack Types

Burp Suite Intruder offers four **attack types**, each suited for different testing needs.

### 1. Sniper
- Inserts one payload at a time into one position.  
- Ideal for single-parameter tests (e.g., brute-forcing a password field).  
Each payload replaces all available insertion points sequentially.

**Request generation example:**
```http
username=§pentester§&password=§Expl01ted§
```
Results in distinct requests for each word in a wordlist.

---

### 2. Battering Ram
- The same payload is inserted into all positions simultaneously.
- Commonly used for **race condition testing** or when multiple fields expect identical input.

Example:
```
username=§test§&password=§test§
```

---

### 3. Pitchfork
- Allows **multiple payload sets**, one for each insertion point.
- Each list progresses in sync, pairing related entries across positions.
  - Useful for credential-stuffing: testing correlated username and password pairs.

Example:

| Request | Username | Password  |
|----------|-----------|-----------|
| 1 | joel | J03l |
| 2 | harriet | Emma1815 |
| 3 | alex | Sk1ll 

---

### 4. Cluster Bomb
- Combines all payloads in every possible combination.
- Tests every entry across lists (Cartesian product).  
Effective for brute-forcing unknown username-password mappings.

**Caution:**  
The number of requests grows quickly (PayloadSet₁ × PayloadSet₂ × ... × PayloadSetₙ).

Example:

| Request | Username | Password |
|---------|----------|----------|
| joel | J03l |
| harriet | J03l |
| alex | Sk1ll |

---

## Practical Applications
- **Brute-forcing authentication forms**  
  Using the *Sniper* or *Pitchfork* modes to test login pairs.
- **Fuzzing query parameters**  
  Detects errors that may reveal SQL injection vulnerabilities.  
  Example: `id=§1§` → `id=§' OR 1=1--§`
- **Testing for race conditions**  
  Use *Battering Ram* for concurrent identical payloads.

Intruder can be chained with findings from [[Burp Suite - Repeater]] to automate repetitive payload testing once a vulnerability vector has been manually confirmed.

---

## Example Workflow

### Step 1 — Capture a Request
Intercept a request from **Proxy** and send it to Intruder (`Ctrl + I`).

### Step 2 — Define Positions
Mark the desired fields in the request body or URL using §.

### Step 3 — Add Payloads
Load or paste payloads (e.g., usernames, endpoints, or fuzzing strings).

### Step 4 — Choose an Attack Type
Select *Sniper*, *Battering Ram*, *Pitchfork*, or *Cluster Bomb*.

### Step 5 — Start Attack
Review the responses for differences (status codes, content length, or keywords).

---

## Final Notes
Burp Suite Intruder helps shift from **manual discovery** to **automated testing**, filling the gap between quick checks using [[TOOLS/Burp Suite/Burp Suite - Repeater]] and large-scale fuzzing with external tools like Wfuzz or FFUF.

While rate-limiting can make the Community Edition slower, its configurability makes it excellent for deliberate, controlled testing workflows.  
Carefully naming attack configurations (“Login Test – Pitchfork”, “SQLi – Sniper”) helps maintain organization during active engagements.

---

### Related Notes
- [[TOOLS/Burp Suite/Burp Suite - Repeater]] — For manual payload validation before automation.
- [[WEB/Vulnerabilities/SQL Injection/SQLi - Introduction]] — Intruder use in automating SQLi detection.
- [[Defensive/INDEX]] — For insights on input validation and mitigation against brute-force or fuzzing attacks.
