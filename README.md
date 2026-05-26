# Blue Team Python — SOC Detection Tools

> Python-based security tools for log analysis, threat detection 
> and security automation. Built from scratch with deep understanding 
> of every concept — no frameworks, no shortcuts.

---

## About This Repository

This repository documents my journey mastering Python specifically 
for blue team cybersecurity work. Every tool here was built from 
the ground up with a focus on:

- Understanding WHY the code works, not just HOW to write it
- Connecting every Python concept to real SOC scenarios
- Building detection logic the way professional tools build it
- Thinking like both an attacker and a defender simultaneously

---

## Repository Structure

| Phase | Topic | Status |
|-------|-------|--------|
| Phase 1 | Core Python Foundations | ✅ Complete |
| Phase 2 | Data Handling & Log Analysis | ✅ Complete |
| Phase 3 | File Handling & Real Log Formats | ✅ Complete |
| Phase 4 | Functions & Modular Scripting | ✅ Complete |
| Phase 5 | System & Network Interaction | 🔄 In Progress |
| Phase 6 | Advanced Blue Team Logic | ⏳ Upcoming |
| Phase 7 | Advanced Python for Security | ⏳ Upcoming |

---

## Tools Built So Far

### Generic Log Analyzer
Processes server logs, tracks failed logins per IP, detects 
brute force patterns using behavioral thresholds, flags and 
records malformed log entries with graceful degradation.

### SSH Log Analyzer
Parses real Linux SSH authentication logs. Extracts attacker 
IPs and targeted usernames. Detects brute force attempts with 
two severity levels — WARNING and CRITICAL. Accepts any log 
file as a command line argument.

### Apache Log Analyzer
Parses real Apache web server logs. Detects directory scanning 
via 404 error patterns. Detects login brute force via 401 error 
patterns. Reports structured SOC-style output with severity levels.

---

## Key Concepts Demonstrated

- **Defensive coding** — scripts never crash on malformed input
- **Graceful degradation** — bad logs are recorded, not silently dropped
- **Behavioral analysis** — tracking patterns across multiple events
- **Severity levels** — separating noise from real threats
- **Modular design** — functions with single responsibilities
- **CLI tools** — scripts that accept runtime arguments
- **Real log parsing** — SSH, Apache, generic log formats

---

## Background

Self-directed cybersecurity learning focused on blue team work, 
SOC analysis and detection engineering. Building toward a 
Masters in Cybersecurity with a foundation in real tool development 
rather than surface-level tool usage.

---

## Connect

Built by Onyina — aspiring Detection Engineer and SOC Analyst.
