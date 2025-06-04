
# Jojo's Hospital 🏥 – KC7 readme

> **Focus:** Host-based analysis, lateral movement, credential theft  
> **Status:** ✅ Completed

---

## 🧠 Scenario

A hospital network was suspected of being breached. You were tasked with investigating potential lateral movement, credential theft, and internal system compromise.

---

## 🔎 Steps Taken

1. **Initial Alert Review**
   - Investigated suspicious login attempts from a patient record system.
   - Used KQL to identify failed logins followed by a successful escalation.

2. **Process & Command Tracking**
   - Queried command execution logs for credential dumping tools and unusual binaries.
   - Detected tools often associated with credential harvesting.

3. **Lateral Movement Tracing**
   - Queried RDP and remote execution logs.
   - Built timeline of the attacker moving across machines within the hospital network.

---

## 🔐 Outcome

- Identified credential theft and lateral movement from one host to another.
- Mapped adversary actions across several internal systems.
- Demonstrated correlation of logs with timestamp-based joins.

---

## 🧰 Tools Used

- **KQL**
- Windows Security Event logs inside Azure Data Explorer
- Remote access + process creation logs

---

*Reinforced understanding of attacker movement and credential-based attacks in an enterprise.*
