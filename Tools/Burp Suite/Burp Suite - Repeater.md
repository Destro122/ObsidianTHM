## Overview
**Burp Suite Repeater** is a tool used to manually modify and resend intercepted HTTP requests to a target.  
It allows testers to:
- Capture a live request through the Proxy module.  
- Edit request parameters, headers, or body content.  
- Re-send the request multiple times to observe server responses.  

This makes Repeater ideal for testing injection vulnerabilities, bypassing filters, and exploring endpoints manually.

---

## Interface Overview

### Request List
Displays all active requests currently loaded into Repeater. Each new request appears as a tab for easy management.

### Request Controls
Located below the list, these buttons allow:
- **Send**: Send the current request.
- **Cancel**: Stop a pending request.
- **Navigate history**: View previous request versions using forward/back arrows.

### Request & Response Panel
The main section showing the editable **Request** (left) and the corresponding **Response** (right).  
You can switch between:
- **Pretty**: Formatted for readability.
- **Raw**: The unmodified content.
- **Hex**: Byte-level view (useful for binary data).
- **Render**: Graphical rendering of web pages.

### Layout Options
Found top-right of the main panel, allowing horizontal, vertical, or tabbed display of requests and responses.

### Target Field
Displays the host or IP of the active target. When requests are sent from **Proxy**, the target fills automatically.

### Inspector
Located on the far right, the **Inspector** module provides an organized interface for request manipulation:
- **Request Attributes**: Modify the URL path, HTTP method (GET/POST), or protocol version (HTTP/1 – HTTP/2).  
- **Query Parameters**: Shows GET variables.  
- **Body Parameters**: Shows POST data and form inputs.  
- **Cookies**: Allows viewing and editing cookies sent to the server.  
- **Headers**: Add, remove, or modify request headers easily.  
- **Response Headers**: Non-editable; display server responses for analysis.

---

## Workflow Integration

1. **Capture a Request** in Burp **Proxy**.  
2. **Send to Repeater**:  
   - Right-click the captured request → *Send to Repeater*  
   - Or use shortcut **Ctrl + R**.  
3. **Edit Parameters**: In the Request view, modify headers, parameters, or body.  
4. **Press Send**: Observe how the server responds to each modification.  
5. **Cycle through history**: Review each variation and its results.

---

## Example Exercise

### Step 1: Basic Request
Send an intercepted request to `http://MACHINE_IP/` and view its HTML response in “Pretty” view.

### Step 2: Modify Headers
Add a custom header to your request:
```http
FlagAuthorised: True
```
Request example:
```http
GET / HTTP/1.1  
Host: MACHINE_IP  
User-Agent: Mozilla/5.0  
Connection: keep-alive  
FlagAuthorised: True
```

### Step 3: Send and Observe
After sending, check if the new header affects the server response (e.g., reveals new content).

---

## Display Modes
| Mode | Description |
|------|--------------|
| **Pretty** | Formatted readable version of request/response. |
| **Raw** | Full unmodified HTTP content. |
| **Hex** | Byte-oriented view useful for binary inspection. |
| **Render** | Browser-like rendering of HTML pages. |

The **Show non-printable characters (\\n)** feature lets testers visualize carriage returns and line breaks, helpful when debugging malformed headers.

---

## Using Repeater for Vulnerability Testing

Repeater is commonly used for:
- **Manual SQL Injection** testing (`id=1' and '1'='1`).
- **Authentication bypass attempts**.
- **Header manipulation and filter testing**.
- **Fuzzing endpoints** (when combined with macros or custom scripts).

---
## Final Notes
Burp Suite Repeater is indispensable for manual exploitation.  
It bridges observation, experimentation, and exploitation in one interface — perfect for exploring vulnerabilities like:
- [[SQLi - Introduction]]
- [[Command Injection]]
- Header-based bypasses