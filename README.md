# 🎯 AWS Honeypot Deployment & Attack Analysis

This project documents the deployment of a [T-Pot](https://github.com/telekom-security/tpotce) honeypot on an AWS EC2 instance to observe, log, and analyze malicious behavior.

---

## 📌 Objective

Deploy a honeypot on an AWS server, collect threat data, and analyze attack methods and trends to inform future defensive strategies.

![Mock Form](https://www.phishy.cloud/assets/img/proj/mock6.jpg)

---

## 🛠️ Tools & Technologies

- AWS EC2
- T-Pot Honeypot (by Deutsche Telekom)
- ELK Stack
- GitHub
- Bash / Linux / SSH
- Virtualization & Docker
- AWS Security Groups & Inbound Rules

---

## 📖 Project Overview

Honeypots are decoy systems designed to attract attackers, monitor their actions, and collect intelligence without compromising real infrastructure. This project used T-Pot, a full-featured honeypot platform, hosted on an AWS EC2 instance to observe intrusion attempts and inform future defensive posture.

---

## ⚙️ Implementation Steps

### 1. ✅ AWS EC2 Instance Creation
- **AMI**: Debian 11
- **Instance Type**: `t3.xlarge` to support ELK and containerized honeypots
- **Storage**: 128 GiB (gp2)
- **Access**: New SSH key pair

### 2. 🔧 Server Setup
- Connected to the instance via SSH
- Performed system updates and basic hardening

### 3. 📦 T-Pot Installation
- Installed Git and cloned the T-Pot repository
- Launched the T-Pot installer
- Created a web user for dashboard access
- Rebooted and verified post-installation success

### 4. 🔐 Inbound Rules Configuration
- **SSH Port**: Custom port allowed for remote administration
- **Web Dashboard**: Opened dashboard port for browser access
- **Custom Traffic Rule**: Allowed all IPs to interact with honeypots

### 5. 🧪 Testing the Honeypot
- Connected via SSH to verify system status
- Accessed the web dashboard via IPv4 URL and custom port
- Verified incoming traffic logs and honeypot service activity

### 6. 📊 Data Monitoring & Analysis
- Used the built-in ELK dashboard to track:
  - IP origins
  - Attack frequencies
  - Methods & ports targeted
- Insights helped identify trends and common vulnerabilities

![Mock Form](https://www.phishy.cloud/assets/img/proj/mock7.jpg)

---

## 🧠 Challenges & Lessons Learned

A key challenge was selecting the correct OS version. The T-Pot documentation referenced a different Debian release which caused installation errors. After further testing and community research, Debian 11 was selected, resolving compatibility issues and allowing a successful deployment.

This experience reinforced the importance of environment compatibility and gave me valuable exposure to containerized monitoring systems and real-time threat telemetry.

![Mock Form](https://www.phishy.cloud/assets/img/proj/mock8.jpg)

---

## 🔍 Data Analysis & Next Steps

After 10 days of uptime, collected data revealed consistent attacks from specific IP ranges and countries. Based on this, I began configuring a **Web Application Firewall (WAF)** in AWS to block:

- Known attacker IPs
- Suspicious request patterns
- Traffic targeting vulnerable services

Future enhancements may include integrating automated WAF updates based on honeypot logs, building alerting pipelines, and testing other honeypot platforms.

---

## 📄 License

This project is open source under the [MIT License](LICENSE).

---

## ✉️ Credits

[T-Pot](https://github.com/telekom-security/tpotce) by Deutsche Telekom Security GmbH and walkthrough by RichGerg - built as a lightweight client-side monitoring solution to support lead gen reliability during a high-traffic ad campaign.

