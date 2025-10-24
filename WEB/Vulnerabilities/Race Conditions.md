## Overview
A race condition occurs when multiple operations or threads access and modify a shared resource at the same time in an unsynchronized manner. This can lead to unintended behavior, such as applying multiple discounts or performing unauthorized financial transactions.

Common example: reusing a $10 gift card to pay for a $100 item if requests overlap.

## Key Concepts
- **Program**: Set of instructions to accomplish a task.
- **Process**: A program in execution with memory and states (new, ready, running, waiting, terminated).
- **Thread**: A lightweight unit of execution; multiple threads can run in parallel within a process.
- **Multithreading**: Running multiple threads concurrently to serve multiple clients or tasks faster.

### Example
In a Flask server running single-threaded mode, requests are handled sequentially. In contrast, a multithreaded server (e.g., Gunicorn) spawns multiple worker processes with threads to handle concurrent requests. This concurrency can lead to race conditions if critical sections are not locked correctly.

## Real-world Analogy
Two hosts at a restaurant reserve the same table simultaneously because of a one-minute delay before it is marked “reserved.”  
Similarly, two threads may both act on outdated data before it gets updated — classic race condition behavior.

## Practical Examples
### Example A
- Account balance: $100
- Thread 1 withdraws $45
- Thread 2 withdraws $35 simultaneously → both see $100 and deduct independently  
Result: inconsistent balance due to unsynchronized state update.

### Example B
- Account balance: $75
- Both threads withdraw $50 each → overdraw beyond the actual balance.

These are TOCTOU (Time-of-Check to Time-of-Use) vulnerabilities.


Repeated execution outputs inconsistent results because both threads modify `x` simultaneously.

## Common Causes
- **Parallel execution**: Multiple simultaneous operations on shared states.
- **Database operations**: Concurrent updates on the same data record.
- **Third-party components**: Poor synchronization in integrated APIs or libraries.

## Web Application Context
Most web apps follow a **three-tier architecture**:
1. **Presentation**: Browser (HTML/CSS/JS)
2. **Application**: Server logic (Node.js, Flask, etc.)
3. **Data**: Database layer (MySQL, PostgreSQL, etc.)

Race conditions often appear when multiple concurrent requests pass unguarded logic between these layers.

## Business Logic Examples
- **Money transfer**:
  - Check balance → Execute transfer → Confirm
- **Coupon application**:
  - Validate code → Check constraints → Apply discount
These transitions imply multiple intermediate states where concurrency might allow repeated actions before “finalization.”

## Exploiting with Burp Suite
Tools such as **Burp Suite Repeater** allow sending duplicated POST requests:
1. Capture a single valid transaction (e.g., transfer or coupon apply).
2. Duplicate the request multiple times (20+).
3. Use “Send group in parallel” to trigger simultaneous server handling.

Results:
- Sequential requests: 1–5 successful.
- Parallel requests: All requests succeed (due to short time window overlap).

## Detection
Race conditions are difficult to detect manually. Clues include:
- Unexplained duplicate transactions.
- Multiple uses of single-use tokens or coupons.

## Mitigation
1. **Synchronization mechanisms**: Locks ensuring one thread modifies data at a time.
2. **Atomic operations**: Grouped, indivisible operations that execute without interruption.
3. **Database transactions**: Ensure all related operations succeed or fail as a unit.

