# Solvi Systems 🛰️ – Threat Detection & Incident Response

This lab simulated a realistic enterprise security investigation at "Solvi Systems," where I was tasked with identifying and responding to an active security incident using a variety of tools and techniques.

---

## 🧠 Objective

Investigate a suspicious alert triggered by a user action and determine whether it represents malicious activity, using real-world evidence such as logs and endpoint data.

---

## 🔍 Investigation Steps

1. **Initial Alert Review:**
   - Alert involved suspicious PowerShell activity on a user machine.
   - Cross-referenced user behavior with historical login activity.

2. **Log Analysis:**
   - Used Splunk to trace DNS queries and file access logs.
   - Found connection to a known malicious domain.

3. **IOC Discovery:**
   - Identified MD5 hash of dropped payload.
   - Confirmed with VirusTotal: marked as trojan downloader.

4. **Endpoint Artifacts:**
   - Detected use of `Invoke-WebRequest` to pull malicious script.
   - Lateral movement attempt to domain controller was logged and blocked.

5. **Response Actions:**
   - Quarantined affected host in simulated environment.
   - Wrote report detailing timeline and root cause.

---

## 🧰 Tools Used
- **Splunk** (log correlation)
- **PowerShell command analysis**
- **VirusTotal** (hash checking)
- **MITRE ATT&CK Mapping** (`T1059`, `T1071`, `T1203`)

---

## 🧾 Key Takeaways
- Reinforced SIEM investigation workflow
- Practiced real-world IR triage skills
- Mapped attacker behavior to MITRE framework
- Improved speed at identifying malicious PowerShell activity

---

### 📸 Screenshot (Optional)
> _Add a screenshot here later of the alert screen or Splunk timeline_

---

📝 *This was one of the most advanced and realistic blue team scenarios I’ve completed so far. Would 100% recommend for anyone prepping for SOC analyst roles or CySA+.*
