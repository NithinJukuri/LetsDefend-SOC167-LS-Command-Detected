# 🚨 SOC Alert Investigation Report  
### Alert: SOC167 - **LS Command Detected in Requested URL**

---

## 📅 Event Summary
| Field | Details |
|------|---------|
| **Alert Name** | SOC167 - LS Command Detected in Requested URL |
| **Event ID** | 117 |
| **Event Time** | Feb 27, 2022 — 00:36 AM |
| **Severity** | High |
| **Category** | Web Attack |
| **Device Action** | Allowed |
| **Source IP** | 172.16.17.46 (Internal User) |
| **Destination IP** | 188.114.96.15 (Cloudflare — LetsDefend Blog) |
| **Requested URL** | `https://letsdefend.io/blog/?s=skills` |
| **Trigger Reason** | Rule detected **“ls”** in the URL |

---

## 🕵️ Investigation Steps

### 1️⃣ Checked Raw Proxy Log 🧾
- The request method was `GET`
- No command execution was present
- HTTP status `200` — normal web browsing response

### 2️⃣ Checked VirusTotal Reputation of Destination IP 🌐
| IP | Result |
|----|--------|
| 188.114.96.15 | **0/95 malicious detections** – Cloudflare network |

> Traffic was going to a **legitimate blog website**.

### 3️⃣ Endpoint Activity Analysis 🖥️

#### 🔹 Network Connections
Multiple connections to the same LetsDefend blog domain — **normal website browsing pattern**

#### 🔹 Browser History
| Time | URL |
|------|-----|
| 00:01 | https://letsdefend.io/blog/ |
| 00:05 | SOC Analyst career articles |
| 00:35 | Resume preparation article |
| 00:36 | `/blog/?s=skills` (Triggered alert) |

Looks like the user was **searching blog content**, not exploiting commands.

#### 🔹 Terminal History
Only one harmless command:


---

## 📌 Conclusion

| Criteria | Result |
|---------|--------|
| Malicious Intent | ❌ Not Found |
| Command Execution Attempt | ❌ None |
| Suspicious Related Traffic | ❌ None |
| User Activity | Normal Web Browsing ✔ |

> **The “ls” detected was part of the search term “skills”, not an executed Linux command.**  
> This alert is classified as a **False Positive**.

---

## 📝 Analyst Note
This alert was generated due to the substring **“ls”** inside the benign query parameter `?s=skills` while accessing the official LetsDefend blog. Full investigation of proxy logs, endpoint network traffic, browser history, and VirusTotal results confirmed **no malicious behavior**.

---

## 🏷 Final Classification
> 🟢 **False Positive** — Safe browsing activity, no further action required.

---

## 👨‍💻 Analyst
Jukuri Nithin Kumar  
Cybersecurity Analyst — Hands-on SOC Training @ LetsDefend

