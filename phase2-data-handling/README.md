# Phase 2 — Data Handling & Log Analysis

## Objective

Learn to handle log data the way a SOC analyst handles it —
normalizing, parsing, tracking, and detecting patterns.

---

## Concepts Learned

### String Handling
`.strip()` `.lower()` `.upper()` indexing and slicing.

**Security relevance** — log normalization prevents detection 
bypasses. An attacker typing "FAILED" vs "failed" vs "Failed" 
should all trigger the same detection. Normalization ensures this.

### Log Parsing with .split()
Extracting structured fields from raw text using separators.

```python
parts = log.split(" - ")
ip     = parts[0]
status = parts[1]
```

### Lists
Storing multiple log entries and iterating through them —
the foundation of batch log processing.

### Detection Logic
```python
if "failed" in status:
    # trigger detection
```

### Counting Events
Tracking frequency of security events — the basis of 
threshold-based detection.

### Dictionaries — Critical Milestone
Mapping IPs to behavior counts. The data structure that 
makes behavioral analysis possible.

```python
failed_by_ip = {
    "192.168.1.1": 3,
    "172.16.5.3": 7
}
```

### Defensive Coding
Validating log structure before extraction. Scripts that 
never crash on malformed input.

### Structured Alerting
SOC-style reporting with severity levels.

---

## Security Concepts Mastered

- **Graceful degradation** — detection continues despite bad data
- **Behavioral analysis** — tracking patterns not single events  
- **Severity levels** — WARNING vs CRITICAL based on volume
- **Blind spot awareness** — skipped logs tracked and reported
- **Log injection awareness** — high volume of bad logs = suspicious
