# 📘 VAPT Capstone Project – Portfolio Write-Up

## 🔹 Project Overview

* **Objective:** Conduct a Vulnerability Assessment & Penetration Test (VAPT) for TechShield, simulating attacks against client environments.
* **Goals:**

  * Identify and exploit real-world weaknesses.
  * Adapt methodology as obstacles arose.
  * Perform forensic validation of attack traces.
  * Provide actionable recommendations.

---

## 🔹 Problem-Solving Approach

Instead of rigidly following every tool, I **adapted my testing flow** based on findings:

* Used **Nmap** and **Greenbone** selectively until I found sufficient entry points.
* Skipped unnecessary tools once I had a confirmed vulnerability chain.
* Focused on **validating exploits, not just scanning**.

**Example:**
When `hydra` brute-force attempts against PostgreSQL kept **timing out with rockyou.txt**, I adjusted my approach:

* Reduced syntax complexity.
* Elevated privileges for faster execution.
* Achieved credential access without wasting time on unnecessary retries.

This demonstrated **efficiency + adaptability**, rather than robotic tool use.

---

## 🔹 Key Exploits & Findings

* **SQL Injection (PostgreSQL / DVWA):**

  * Bypassed login authentication.
  * Modified stored credentials (proving account takeover risk).

* **XSS (Stored & Reflected):**

  * Injected dummy text to simulate payload execution.
  * Confirmed script delivery in browser.

* **SMB Exploitation:**

  * Used `smbclient` + Metasploit payloads to gain remote system access.

* **Digital Forensics (Autopsy):**

  * Dummy images were planted to replicate attacker activity.
  * Files were **mounted to the desktop** and not manually accessible — validated with forensic imaging.
  * Proved ability to detect and trace attacker artifacts.

---

## 🔹 Risk Assessment

Findings showed attackers could:

* Compromise databases via weak SQL handling.
* Manipulate user sessions and data via XSS.
* Exploit misconfigured SMB services to gain persistence.
* Leave **forensic footprints** visible only through proper tools (not manual inspection).

---

## 🔹 Recommendations

* **Authentication Hardening:** Strong passwords, MFA, block weak services.
* **Patch & Update:** Apache Tomcat, legacy OS versions, DRb, DistCC.
* **Service Restriction:** Disable `rexec`, Ingreslock, unneeded RMI.
* **Forensic Readiness:** Train staff on forensic tools like Autopsy to validate post-incident activity.

---

## 🔹 Lessons Learned

* **Adaptability matters:** Hydra brute-force issues forced me to rethink syntax and privilege use.
* **Not every tool is needed:** Knowing when to stop scanning and start exploiting saves time and shows efficiency.
* **Forensics prove the story:** Dummy Autopsy images simulated a real attacker presence, making the report more realistic.
* **Red + Blue crossover:** Offensive testing gave insight into detection and post-attack validation.

---
