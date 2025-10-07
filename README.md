# 🔒 Wazuh + Suricata Integration

**Wazuh** and **Suricata** are powerful open-source security tools that, when integrated, deliver a robust and comprehensive security monitoring solution.  
This setup enhances visibility, detection, and response capabilities by combining **network-based** and **host-based** monitoring.

---

## 🚀 Overview of the Integration

### 1. Data Collection and Analysis
- **Suricata** acts as a **Network IDS/IPS**, monitoring traffic for suspicious activities.  
- It uses **signature-based** and **anomaly-based** detection to identify potential threats.  
- **Wazuh** acts as a centralized **Security Information and Event Management (SIEM)** system, collecting and analyzing logs from Suricata and other sources.

### 2. Unified Threat Detection
- Suricata generates network-based alerts and forwards them to Wazuh for aggregation and correlation.  
- This unified system detects complex attacks that span both **network** and **endpoint** environments, reducing false positives and improving accuracy.

### 3. Incident Response and Forensics
- Wazuh enriches Suricata’s network alerts with endpoint data, enabling deeper investigation.  
- Supports **real-time alerting**, **automated responses**, and **detailed forensic reports** for faster remediation.  

### 4. Scalability and Flexibility
- Both tools scale horizontally — ideal for small setups or enterprise environments.  
- Configurable rules, alerts, and reports make it highly adaptable to organizational needs.  

### 5. Enhanced Visibility and Correlation
- Wazuh’s dashboard integrates Suricata alerts alongside host-based events for **a single pane of glass** monitoring.  
- Correlating network and endpoint data helps uncover **multi-stage attacks** and identify root causes efficiently.

---

## ⚙️ Architecture Diagram
*(Optional — you can upload one later in `/docs/architecture-diagram.png`)*  
