# Phase 1 — Core Python Foundations

## What This Phase Covers

The building blocks of Python that everything else depends on.
Every concept here was learned with cybersecurity application in mind.

---

## Concepts Learned

### Variables
Storing and updating values. In security context — tracking 
login attempts, storing IP addresses, holding alert states.

### Data Types
- **Strings** — log lines, IP addresses, usernames
- **Integers** — attempt counts, port numbers, status codes  
- **Booleans** — is this IP blocked? is this log valid?

### Operators
- Arithmetic — counting failed attempts
- Comparison — is count >= threshold?
- Logical — `and`, `or`, `not` for complex detection conditions

### Conditional Logic
`if`, `elif`, `else` — the foundation of every detection rule.
Every alert in a SIEM is fundamentally a conditional statement.

### Loops
- `while` — repeat until condition changes
- `for` — process every item in a collection
- Loop control — `continue` to skip, `break` to stop

---

## Security Concepts Introduced

- Authentication logic and credential validation
- Why generic error messages are safer than specific ones
- Information leakage through system responses
- Brute force mitigation through attempt counting
- State tracking in security systems

---

## Key Security Insight

Every detection rule in the world — whether in Splunk, 
Microsoft Sentinel, or a custom Python script — is built 
from these exact foundations. Conditions, loops, and counters 
are the atoms of detection engineering.
