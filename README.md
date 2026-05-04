Splunk SIEM Lab – Brute Force Attack Detection

Overview

This project demonstrates detection of an SSH brute-force attack using Splunk SIEM. Logs were collected from a Linux system and analyzed to identify failed login attempts and attacker behavior.

---

Tools Used

* Kali Linux (Attacker)
* Ubuntu (Target System)
* Splunk Enterprise
* Hydra
* VMware Workstation

---

Lab Setup

* SSH enabled on Ubuntu machine
* Kali Linux used to perform brute-force attack
* Logs collected from `/var/log/auth.log`
* Logs ingested into Splunk for analysis

---

Attack Simulation

A brute-force SSH attack was performed using Hydra:

```
hydra -l sandeep-pattanaik -P passwords.txt ssh://192.168.x.x
```

---

Detection in Splunk

  Failed Login Detection

```
index=main sourcetype=auth_logs "Failed password"
```

  Attacker IP Identification

```
index=main sourcetype=auth_logs "Failed password"
| rex "from (?<src>\d+\.\d+\.\d+\.\d+)"
| stats count by src
```

   Successful Login Detection

```
index=main sourcetype=auth_logs "Accepted password"
```

---

Results

* Multiple failed login attempts detected
* Attacker IP identified: 192.168.142.128
* Successful login observed after brute-force attack

---

Conclusion

This project demonstrates how Splunk SIEM can detect brute-force attacks by analyzing authentication logs and identifying suspicious patterns.

---

Skills Demonstrated

* SIEM (Splunk)
* Log Analysis
* Cyber Attack Simulation
* Incident Detection
