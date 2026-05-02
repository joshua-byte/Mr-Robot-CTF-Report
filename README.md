# Web Application Penetration Test Case Study – Mr Robot Lab

## 📌 Overview

This project simulates a web application penetration test conducted on the Mr Robot vulnerable machine. The objective was to identify vulnerabilities, exploit weaknesses, and achieve full system compromise.

The assessment demonstrates real-world attack techniques including web enumeration, credential discovery, remote code execution, and privilege escalation.

---

## 🎯 Objectives

* Perform reconnaissance and service enumeration
* Identify web application vulnerabilities
* Exploit authentication and configuration weaknesses
* Gain remote shell access
* Escalate privileges to root

---

## 🧱 Target Environment

* Target Machine: Mr Robot (Vulnerable VM)
* Attacker Machine: Kali Linux
* Environment: Controlled lab setup

---

## ⚔️ Methodology

Reconnaissance → Enumeration → Exploitation → Privilege Escalation → Reporting

---

## 🔍 Attack Surface

* Web Server (HTTP)
* WordPress CMS
* Hidden directories and files

---

## 🔍 Findings

### 🔴 Sensitive Information Disclosure (robots.txt)

* **Severity:** Medium
* **Description:** robots.txt exposed hidden directories and sensitive files
* **Impact:** Enabled discovery of key application paths and credentials

**Proof:**

* Accessed `/robots.txt` revealing hidden paths
<img width="956" height="350" alt="robots txt" src="https://github.com/user-attachments/assets/42fddf5a-4e08-4381-8b21-d032fdf10440" />

---

### 🔴 Credential Exposure & Weak Authentication

* **Severity:** High
* **Description:** Credentials were discoverable through enumeration and reused across services
* **Impact:** Unauthorized access to administrative interface

**Proof:**

* Username discovery via enumeration
* Password cracked using wordlist


### 🔴 Remote Code Execution (Reverse Shell)

* **Severity:** Critical
* **Description:** File upload or command execution vulnerability enabled reverse shell access
* **Impact:** Full control of the target system

**Proof:**

* Reverse shell established and cracking the 2nd hash to recover the 2nd flag
<img width="963" height="374" alt="exploitation_and_2ndkey" src="https://github.com/user-attachments/assets/87298451-4dc5-4525-972f-07177be542b3" />


---

### 🔴 Privilege Escalation (SUID Misconfiguration)

* **Severity:** Critical
* **Description:** Misconfigured SUID binary allowed privilege escalation
* **Impact:** Root-level access achieved

**Proof:**

* Exploited SUID binary
* `whoami → root`
* *(Add screenshot: root shell)*

---

## 🔗 Attack Chain

```id="mrrobotchain"
Reconnaissance
   ↓
robots.txt → Hidden Path Discovery
   ↓
Credential Enumeration → Login Access
   ↓
Reverse Shell → System Access
   ↓
SUID Exploit → Privilege Escalation → Root Access
```

---

## 📊 Impact Assessment

* Unauthorized access to web application
* Credential compromise
* Remote command execution
* Full system takeover

**Business Impact:**
An attacker can gain complete control of the web server, access sensitive data, and escalate privileges to compromise the entire system.

---

## 🛠️ Mitigation & Defensive Measures

* Restrict sensitive file exposure (robots.txt)
* Enforce strong authentication policies
* Validate file uploads and inputs
* Remove unsafe SUID configurations
* Apply principle of least privilege

---

## 🛠️ Tools Used

* Nmap
* Dirb / Gobuster
* Burp Suite (optional if used)
* Netcat
* John the Ripper

---

## 📊 Key Takeaways

* Information disclosure can lead to full compromise
* Weak authentication enables attacker entry
* Web vulnerabilities often lead to system-level compromise
* Misconfigurations are critical security risks

## 🚩 Flags Captured

* Key 1: 073403c8a58a1f80d943455fb30724b9
* Key 2: 822c73956184f694993bede3eb39f959
* Key 3: 04787ddef27c3dee1ee161b21670b4e4

## ⚠️ Note

This project is for educational purposes only.
