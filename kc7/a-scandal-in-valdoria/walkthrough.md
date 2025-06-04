
# A Scandal in Valdoria 👑 – KC7 Walkthrough

> **Focus:** Phishing email investigation, malware detection  
> **Status:** ✅ Completed

---

## 🧠 Scenario

A political figure received a suspicious email that may contain a phishing attachment. Your job: investigate the incident, confirm if malware was delivered, and trace the compromise.

---

## 🔎 Steps Taken

1. **Email Header Analysis**
   - Extracted metadata and sender IP
   - Confirmed sender was spoofed via mismatch in SPF/DKIM

2. **Attachment Inspection**
   - ZIP archive contained a `.doc` file with macros
   - Detected base64-encoded PowerShell dropper embedded

3. **Payload Behavior**
   - Payload contacted a remote server to download secondary malware
   - DNS + NetFlow logs showed communication with known C2 infrastructure

---

## 🔐 Outcome

- Confirmed delivery of malicious macro-based payload
- Documented C2 behavior + artifacts found on host
- Identified TTPs:
  - `T1566.001` (Phishing via Attachment)
  - `T1059.001` (PowerShell)
  - `T1047` (WMI execution)

---

## 🧰 Tools Used

- Email Header Analyzer
- VirusTotal
- PowerShell decoding tools
- Splunk (for host logs)

---

*Excellent case for learning email forensics and lateral movement identification.*
