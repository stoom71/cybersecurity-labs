# KQL 101 🧠 – KC7 readme

> **Focus:** Query development in Kusto Query Language (KQL)  
> **Status:** ✅ Completed

---

## 🧠 Scenario

You were dropped into a simulated security operations environment and had to write KQL queries from scratch to detect security incidents across various log types.

---

## 🔎 Steps Taken

1. **Built Basic Queries**
   - Queried failed logins, filtered by time and usernames.
   - Used `project`, `where`, and `summarize` to visualize patterns.

2. **Joined Datasets**
   - Combined multiple log sources (auth, process, network) to identify patterns.
   - Used `join` and `extend` to enrich event data.

3. **Detection Building**
   - Created detections for unusual admin role creation.
   - Detected base64-encoded commands commonly used in malicious activity.

---


