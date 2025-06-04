# A Scandal in Valdoria 👑 – KC7 readme

> **Focus:** Phishing email detection, user behavior analysis  
> **Status:** ✅ Completed

---

## 🧠 Scenario

You received a tip that a political figure might have been phished. Your task was to investigate any suspicious email activity and confirm if compromise occurred.

---

## 🔎 Steps Taken

1. **Email Delivery Log Querying**
   - Queried message trace logs to find suspicious sender information.
   - Filtered results based on external sender domains and abnormal subject lines.

2. **User Activity Analysis**
   - Queried endpoint logs to detect execution of downloaded files shortly after email delivery.
   - Used KQL to search for unusual command-line activity by the recipient.

3. **IOC Identification**
   - Identified suspicious filename and hash values linked to phishing attachments.
   - Used pattern matching in KQL to detect repeated execution attempts.

---

## 🔐 Outcome

- Verified phishing email led to execution of a potentially malicious file.
- Confirmed user was compromised via attachment-based phishing.
- Noted attacker behavior aligning with credential theft and persistence.

---

## 🧰 Tools Used

- **KQL (Kusto Query Language)**
- KC7-provided message trace and endpoint log datasets
- Email metadata queries

---

*Showcased ability to investigate end-to-end phishing incidents using only KQL and logs.*
