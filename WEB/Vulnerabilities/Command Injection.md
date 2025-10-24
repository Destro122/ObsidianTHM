## Overview
Command Injection is a vulnerability that allows the execution of unintended system commands through user input. Attackers exploit applications that integrate user data directly into operating system calls. The commands are executed with the same privileges as the application process.

Also referred to as Remote Code Execution (RCE), this flaw can lead to full system compromise, allowing access to sensitive files, credentials, and the host system.

## Root Cause
This vulnerability occurs when developers use functions that pass unsafe user input to the OS, such as:
- `system()`  
- `exec()`  
- `passthru()`  
Applications written in PHP, Python, or NodeJS are particularly susceptible when failing to sanitize or validate user inputs.

## Example Scenario
``system("grep " . $title . " songtitle.txt");`` 

If a user submits `The Beatles; whoami`, the `whoami` command executes on the host OS due to unsanitized concatenation.

## Detection Types
Two primary forms of Command Injection exist.

### Blind Injection
- The web application executes a command without direct output.  
- Use time-based payloads:
  - `ping -c 10 127.0.0.1`
  - `sleep 10`
- Detect through delayed server response or behavioral changes.

### Verbose Injection
- The output is visible on the web application.  
- Example payload:
  - `; whoami`
  - The application will display the execution result directly on the page.

## Payload Examples

### Linux
| Payload | Description |
|----------|-------------|
| `whoami` | Identify user account the app runs under. |
| `ls` | List directory contents. |
| `ping <IP>` | Delay-based detection. |
| `sleep <seconds>` | Alternative delay method. |
| `nc` | Reverse shell payload for remote access. |

### Windows
| Payload | Description |
|----------|-------------|
| `whoami` | Identify user privileges. |
| `dir` | List current directory contents. |
| `ping <IP>` | Test for delays. |
| `timeout <seconds>` | Used when `ping` unavailable. |

## Filter Bypass
Applications may apply input filters (e.g., removing quotes or special characters).  
Attackers can bypass them by using:
- Hexadecimal or encoded representations (`\x27` instead of `'`)  
- Alternative operators (`|`, `&`, `||`, `&&`).

## Mitigation
### Input Sanitization
Restrict input to strictly defined acceptable patterns.
Example in PHP:
```php
if (preg_match('/^[0-9]+$/', $_POST['input'])) {  
system($_POST['input']);  }
```

### Minimal Use of System Functions
Avoid use of dangerous functions like:
- `system()`, `exec()`, `shell_exec()`, `passthru()`
### Parameterization
Do not concatenate input values directly into OS commands.
Instead, use pre-defined safe operations or language-specific system APIs.

---

Related tools: [[TOOLS/Burp Suite/Burp Suite - Repeater]] can aid in crafting repeated payloads.
