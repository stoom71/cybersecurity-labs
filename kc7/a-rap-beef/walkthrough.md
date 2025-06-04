# A Rap Beef 🎤 – KC7 Walkthrough

> **Focus:** SOC fundamentals, alert triage, log correlation  
> **Status:** ✅ Completed

---

## 🧠 Scenario

A user in a simulated music production company reported unusual behavior. You were tasked with investigating alerts, identifying malicious activity, and understanding the incident timeline.

---

## 🔎 Steps Taken

1. **Analyzed Initial Alert**
   - Reviewed triggered Splunk alerts related to PowerShell usage and unknown process creation
   - Flagged suspicious command: `Invoke-WebRequest`

2. **Reviewed Logs**
   - Investigated DNS queries pointing to `suspiciousdomain.biz`
   - Found evidence of a ZIP file being downloaded via PowerShell

3. **Timeline Construction**
   - Matched DNS logs + command-line execution with login activity
   - Mapped attacker behavior over a ~30 min window

---

## 🔐 Outcome

- Confirmed phishing link led to a downloaded payload
- Detected persistence mechanism using Scheduled Task
- Documented attacker TTPs aligned with:
  - `T1059.001` (PowerShell)
  - `T1071` (C2 over DNS)

---

## 🧰 Tools Used

- Splunk
- Windows Security Logs
- PowerShell command forensics

---

*Great intro to log triage, attacker behavior analysis, and report writing.*
