# Phase 3 — File Handling & Real Log Formats

## Objective

Move from hardcoded test data to reading real log files 
from disk — the way actual SOC tools operate.

---

## Concepts Learned

### File Handling
```python
with open("logs.txt", "r") as file:
    for line in file:
        log = line.strip()
```

**`with`** — automatically closes the file when done.
**`strip()`** — removes invisible newline characters `\n` 
that break detection logic.

### Real Log Formats Parsed

#### Linux SSH Authentication Logs

Jan 10 06:55:48 server sshd[1234]: Failed password for root from 192.168.1.1 port 22 ssh2

Extraction by keyword splitting — `"from "` for IP, 
`"for "` for username.

#### Apache Web Server Logs

192.168.1.1 - - [date] "GET /admin HTTP/1.1" 404 512

Extraction by index position after splitting by space.
IP at index 0, status code at index 8, path at index 6.

---

## Tools Built

### ssh_analyzer.py
- Reads real SSH auth logs from disk
- Extracts attacker IP and targeted username
- Tracks failed attempts per IP
- Tracks which usernames are targeted
- Severity levels: WARNING (3+) CRITICAL (6+)
- Records and reports all malformed lines

### apache_log_analyzer.py
- Reads real Apache access logs from disk
- Detects directory scanning via 404 patterns
- Detects brute force login via 401 patterns
- Structured SOC report output

---

## Key Security Insight

Different log formats require different parsing strategies.
SSH logs need keyword-based extraction.
Apache logs need index-based extraction.

This is exactly what SIEM normalization engines do at scale —
they apply format-specific parsers to convert raw logs into 
structured, analyzable data. These tools demonstrate that 
concept from first principles.

---

## Attack Patterns Detected

| Pattern | Indicator | Detection Method |
|---------|-----------|-----------------|
| SSH Brute Force | Multiple failed passwords from one IP | Count per IP >= threshold |
| Username Targeting | Same account attacked repeatedly | Count per username >= threshold |
| Directory Scanning | High volume of 404 errors | Count 404s per IP >= threshold |
| Login Brute Force | High volume of 401 errors | Count 401s per IP >= threshold |
