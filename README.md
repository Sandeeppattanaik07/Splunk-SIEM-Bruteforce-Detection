# 🔐 Splunk SIEM – Brute Force Attack Detection

## 📌 Project Overview

This project demonstrates how a **brute force SSH attack** can be detected using **Splunk SIEM**.
Logs are collected from an Ubuntu system and analyzed to identify multiple failed login attempts and attacker activity.

---

## 🛠️ Tools & Technologies

* Splunk Enterprise (SIEM)
* Ubuntu Linux (Target Machine)
* Kali Linux (Attacker Machine)
* Hydra (Brute Force Tool)
* SSH Logs (`auth.log`)

---

## ⚙️ Project Workflow

### 1️⃣ Target System Setup

<img src="screenshots/1_target_ip.png" width="700">
---

### 2️⃣ SSH Service Running

<img src="screenshots/2_ssh_running.png" width="700">
---

### 3️⃣ SSH Login Attempt

<img src="screenshots/3_ssh_login.png" width="700">
---

### 4️⃣ Brute Force Attack using Hydra

<img src="screenshots/4_hydra_attack.png" width="700">
---

### 5️⃣ Splunk Setup

<img src="screenshots/5_splunk_setup.png" width="700">
---

### 6️⃣ Data Ingestion (auth logs)

<img src="screenshots/6_data_ingestion.png" width="700">
---

### 7️⃣ Failed Login Detection

<img src="screenshots/7_failed_logins.png" width="700">
---

### 8️⃣ Attacker IP Identification

<img src="screenshots/8_attacker_ip.png" width="700">
---

### 9️⃣ Successful Login Detection

<img src="screenshots/9_successful_login.png" width="700">

---

## 🔍 Splunk Query Used

```spl
index=main sourcetype=auth_logs "Failed password"
| rex "from (?<src>\d+\.\d+\.\d+\.\d+)"
| stats count by src
```

---

## 🚨 Detection Logic

* Multiple failed login attempts from same IP
* Extraction of attacker IP using `rex`
* Aggregation using `stats count`
* Identification of brute force pattern

---

## 🎯 Key Learnings

* Log analysis using Splunk
* Detection of brute force attacks
* Understanding SSH authentication logs
* Creating SIEM detection queries

---

## 🔗 Related Project

👉 [Cyber Security Maturity Assessment (NALCO)](https://github.com/Sandeeppattanaik07/Cyber-Security-Maturity-Assessment-NALCO)

---
## 📌 Conclusion

This project showcases how SIEM tools like Splunk can effectively detect brute force attacks by analyzing authentication logs and identifying suspicious patterns.

---
