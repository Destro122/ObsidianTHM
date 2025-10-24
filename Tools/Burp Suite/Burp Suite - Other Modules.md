## Overview
Beyond the well-known [[Burp Suite - Repeater]] and [[Burp Suite - Intruder]] tools, Burp Suite provides additional modules that streamline many manual tasks.  
This note covers the following four modules:

1. **Decoder** — Encode, decode, and hash data.
2. **Comparer** — Compare content differences at word or byte level.
3. **Sequencer** — Analyze randomness and entropy of tokens.
4. **Organizer** — Store, annotate, and manage HTTP requests for reporting and workflow tracking.

Although these utilities may appear simple, mastering them inside Burp saves significant time, especially during manual web testing or vulnerability replication.

---

## Decoder
**Decoder** allows users to transform data directly inside Burp Suite.  
It can:
- Encode and decode intercepted data.
- Create hashsums.
- Automatically decode nested data (similar to the “Magic” feature in CyberChef).

To use it, navigate to the Decoder tab and paste your data.  
The interface offers several transformation options, all supporting *Send to Decoder* from any Burp component.

### Common Encoding/Decoding Types
- **Plain:** Raw text with no transformation.  
- **URL:** Converts unsafe characters to %‑encoded form (e.g., `/` → `%2F`).  
- **HTML Entities:** Escapes unsafe characters (e.g., `"` → `&quot;`).  
- **Base64:** Converts data into ASCII‑safe encoding for web transfers.  
- **ASCII Hex:** Converts ASCII text to hexadecimal (e.g., “A” → `41`).  
- **Hex, Octal, Binary:** Numeric conversions between common bases.  
- **Gzip:** Useful for compressing or decompressing captured content.

These methods can be combined, for instance: encoding text to ASCII Hex and then to Octal for layered testing.

### Smart Decode
The **Smart Decode** feature automatically attempts recursive decoding until plaintext is reached — ideal for quickly unveiling encoded payloads.

### Hashing
Decoder can also generate hashes using a large list of algorithms (e.g., MD5, SHA‑1, SHA‑256).  
Hashing provides a one‑way signature of data — useful for verifying integrity or testing password hashing approaches.  

While [[SQLi - Introduction]] and [[Command Injection]] exploitation rely on understanding data encoding and parameter handling, Decoder helps quickly prepare payloads in the required format (URL‑encoded, Base64, etc.).

---

## Comparer
**Comparer** lets you visually or byte‑compare two data sets (requests, responses, or payloads).  
It’s often used to:
- Detect small differences between parameter responses.
- Spot behavioral changes when fuzzing with [[Burp Suite - Intruder]].
- Confirm that a payload bypassed filtering.

### Interface Overview
- **Data list:** Store multiple loaded items from the clipboard or files.  
- **Comparison options:** Compare by *Words* or *Bytes*.
- **Results view:** Highlights added, removed, and modified segments with color coding.

You can quickly send any request or response to Comparer with *Send to Comparer* and analyze server behavior across versions.

---

## Sequencer
**Sequencer** analyzes the randomness of security tokens (such as session cookies or CSRF tokens).  
Predictable or low‑entropy tokens indicate insecure token generation.

### Methods
- **Live Capture:** Continuously requests new tokens to analyze randomness from live responses.  
- **Manual Load:** Imports pre‑collected token lists for review without making network requests.

### Report
Sequencer outputs an **Entropy Report** containing:
- **Overall Result:** Quick quality rating of token randomness.  
- **Effective Entropy:** Measured bits of unpredictability (e.g., 117 bits indicates strong security).  
- **Reliability:** Confidence percentage, usually ≥ 99%.  
- **Character & Bit Analysis:** Per‑position pattern review.

Sequencer is particularly valuable for validation of authentication tokens or recovering weak session management vulnerabilities (an area often linked to flawed logic similar to those in [[Race Conditions]]).

---

## Organizer
**Organizer** serves as a built‑in request management system.  
Unlike [[Burp Suite - Repeater]], which focuses on editing or replaying requests, Organizer is a tracking tool designed to help analysts manage and comment on captured traffic.

### Capabilities
- Store requests or responses needing follow‑up or reporting.
- Send requests directly from any Burp module using *Send to Organizer (Ctrl + O)*.
- Add notes, workflow status, and timestamps for each item.

Organizer displays all stored requests in a sortable table (with columns for tool source, method, URL, response code, size, and notes).  
Selecting a record shows a read‑only view of both request and response — a convenient way to document findings without juggling external note files.

---

## Final Notes
Mastering these “secondary” modules of Burp Suite boosts efficiency during manual testing sessions.  
They integrate fluidly with core components like Repeater and Intruder:

- Decoder assists in crafting and encoding payloads.
- Comparer helps analyze subtle differences during [[SQLi - Types]] or WAF bypass trials.
- Sequencer evaluates token security to uncover weak session randomness.
- Organizer organizes test data for structured reporting.

These modules may not be as flashy as [[Burp Suite - Intruder]] or [[Burp Suite - Repeater]], but they are essential for smooth, professional‑grade workflow automation within Burp Suite.