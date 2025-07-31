# FIM-Wazuh-Report-
This Repository includes the task given by  ITSOLERA Pvt Includes Report with detailed analysis and workflow of the FIM with Wazuh (SEIM ) SOC Cybersecurity
# 🛡️ Wazuh Setup with File Integrity Monitoring (FIM) By Nasir Sharif 

This project demonstrates the deployment of the **Wazuh Security Platform** to collect real-time logs and implement **File Integrity Monitoring (FIM)** for early detection of unauthorized system changes. This foundational setup enables advanced threat detection, log analysis, and SOC-like monitoring for learning or production environments.

## 📌 Project Goals

- Deploy and configure the Wazuh Manager, Dashboard, and Agent.
- Establish secure communication between all components.
- Enable File Integrity Monitoring to detect file changes in real-time.
- Tune FIM to balance alert sensitivity and reduce false positives.
- Lay the groundwork for future advanced security monitoring tasks.

---

## 🔧 Components

- **Wazuh Manager** (Linux OVA)
- **Wazuh Dashboard** (OpenSearch-based web UI)
- **Wazuh Agent** (Deployed on Windows 10)
- **VirtualBox** (for running Wazuh OVA)
- **Windows 10 VM** (Monitored endpoint)

---

## 📂 Directory Structure
.
├── README.md
├── screenshots/
│ ├── dashboard-overview.png
│ └── fim-alert-example.png
├── wazuh-configuration/
│ ├── ossec.conf (Linux)
│ └── ossec.conf (Windows Agent)
└── fim/
├── monitored-paths.txt
└── fim-alerts.json


## ⚙️ Configuration Overview

### 🖥️ Wazuh Manager (OVA)
- Deployed using VirtualBox
- Enabled guest additions and clipboard sharing for easy config updates

### 📋 File Integrity Monitoring (FIM)

**Monitored Paths:**
- `C:\Windows\System32\`
- `C:\Users\Public\Documents\`

**Polling Interval:**
- Every 5 seconds

**Windows Agent ossec.conf Snippet:**
```xml
<syscheck>
  <directories check_all="yes" realtime="yes" report_changes="yes">C:\Windows\System32</directories>
  <directories check_all="yes" realtime="yes" report_changes="yes">C:\Users\Public\Documents</directories>
  <frequency>5</frequency>
</syscheck>

📊 Dashboard Access
URL: https://<your-vm-ip>:5601

Default Credentials:

Username: admin

Password: admin (Change immediately in production)

🧪 Test Case
To validate FIM:

Navigate to C:\Windows\System32\ or C:\Users\Public\Documents\

Create or edit a file (e.g., test.txt)

Within 5 seconds, check the Wazuh Dashboard for a new alert.

📷 Screenshots

Wazuh Dashboard with live alerts from FIM

📚 Future Work
Integration with Suricata for network intrusion detection

Log forwarding to external SIEM

MITRE ATT&CK correlation

Scheduled compliance auditing

📄 License
This project is open-source and licensed under the MIT License.

🤝 Contributing
Pull requests and contributions are welcome! If you find issues or want to enhance this repo, feel free to fork and submit a PR.

🔗 Connect
LinkedIn: Nasir Sharif 

GitHub: @Nasir-Sharif


