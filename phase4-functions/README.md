# Phase 4 — Functions & Modular Scripting

## Objective

Transform working scripts into professional tools using 
functions — reusable, named blocks of logic that each 
do one job cleanly.

---

## Why Functions Matter In Security Tools

Without functions — one long block of tangled code. A bug 
fixed in one script stays broken in others. Logic is 
inconsistent across tools. Detection gaps appear silently.

With functions — fix a bug once, fixed everywhere. Logic 
is consistent. Code reads like plain English. Tools are 
genuinely reusable.

---

## Concepts Learned

### Defining Functions
```python
def function_name(parameters):
    # logic
    return result
```

### Parameters vs Arguments
- Parameter — the placeholder in the definition
- Argument — the real value passed when calling

### Return Values
Functions hand results back to the caller.
Multiple values can be returned simultaneously.

```python
def extract_fields(log):
    ip       = log.split("from ")[1].split(" ")[0]
    username = log.split("for ")[1].split(" ")[0]
    status   = "failed" if "Failed password" in log else "accepted"
    return ip, username, status

ip, username, status = extract_fields(log)
```

### Three Zone Structure
Zone 1 — Function definitions  (top)
Zone 2 — Main logic            (middle)
Zone 3 — Report                (bottom)

### Command Line Arguments with sys.argv
```python
import sys

if len(sys.argv) < 2:
    print("[ERROR] No log file provided.")
    print("Usage: python ssh_analyzer.py <logfile>")
    sys.exit()

filename = sys.argv[1]
```

Run any log file without editing code:
python ssh_analyzer.py monday_auth.log
python ssh_analyzer.py tuesday_auth.log
---

## Tools Built

### ssh_analyzer.py — Final Version
Full modular SSH log analyzer with four functions:

| Function | Input | Output |
|----------|-------|--------|
| `is_valid_log(log)` | log line | True or False |
| `extract_fields(log)` | log line | ip, username, status |
| `update_count(dict, key)` | dictionary + key | updates count |
| `print_report(...)` | all collected data | SOC report |

Accepts any log file as a CLI argument.
Never crashes on malformed input.
Reports all skipped lines with count and warning.

---

## Key Security Insight

Modular detection tools are maintainable detection tools.
When detection logic lives in one function, it is tested once,
trusted everywhere. Inconsistent detection logic across 
multiple scripts creates gaps that attackers can fall through.

Professional detection engineers write functions first,
scripts second.
