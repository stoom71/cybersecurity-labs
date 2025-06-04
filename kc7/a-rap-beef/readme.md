# A Rap Beef 🎤 – KC7 readme

> **Focus:** SOC fundamentals, alert triage, KQL-based log investigation  
> **Status:** ✅ Completed

---

## 🧠 Scenario

A user in a simulated music production company triggered an alert. Your job was to investigate suspicious behavior by querying log data using KQL.

---

## 🔎 Steps Taken

1. **Alert Review**
   - Investigated a triggered alert related to suspicious user behavior.
   - Used KQL to query authentication logs and correlated them with command-line events.

2. **Log Analysis**
   - Identified execution of an unusual command using `Invoke-WebRequest`
   - Queried process creation logs to see what scripts were launched

3. **Timeline Construction**
   - Built a timeline of the attacker’s activity across several systems using event timestamps.

---

## 🔐 Outcome

- Traced execution of a malicious script used to download further payloads.
- Mapped activity to common attack techniques (e.g. initial access + execution)
- Demonstrated ability to pivot across tables using join and summarize in KQL

---

## 🧰 Tools Used

- **KQL (Kusto Query Language)**
- Azure Data Explorer logs
- Windows event data within the KC7 platform

---

*Solid intro to threat detection and alert investigation using query-based analysis.*
