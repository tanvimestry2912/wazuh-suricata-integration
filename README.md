# 🛡️ Suricata IDS Integration with Wazuh

## 📘 Project Description
This project demonstrates how to deploy and configure **Suricata** as a Network Intrusion Detection System (NIDS) and integrate it with **Wazuh** for centralized log monitoring and alert visualization.

Suricata monitors network traffic for suspicious activities using predefined rule sets, while Wazuh collects and analyzes Suricata’s alert logs (`eve.json`) to generate real-time security insights.

---

## ⚙️ Steps Overview

### 1️⃣ Install Suricata
```bash
sudo apt-get install suricata -y
2️⃣ Download Suricata Rules
bash
Copy code
cd /tmp
sudo curl -LO https://rules.emergingthreats.net/open/suricata-6.0.8/emerging.rules.tar.gz
3️⃣ Extract and Move Rules
bash
Copy code
sudo tar -xvzf emerging.rules.tar.gz
sudo mv rules/*.rules /etc/suricata/rules/
sudo chmod 777 /etc/suricata/rules/*.rules
4️⃣ Configure suricata.yaml
Open configuration file:

bash
Copy code
sudo nano /etc/suricata/suricata.yaml
Update network variables:
yaml
Copy code
HOME_NET: "192.168.100.0/24"
EXTERNAL_NET: "any"
Define rule file path:
yaml
Copy code
default-rule-path: /etc/suricata/rules
rule-files:
  - "*.rules"
Set network interface:
(Find interface name using ifconfig, e.g., enp0s3)

yaml
Copy code
af-packet:
  - interface: enp0s3
Save and exit (Ctrl + O, Enter, Ctrl + X).

5️⃣ Restart and Enable Suricata
bash
Copy code
sudo systemctl restart suricata
sudo systemctl enable suricata
6️⃣ Enable Promiscuous Mode in VirtualBox
Go to:

mathematica
Copy code
Settings → Network → Adapter → Advanced → Promiscuous Mode → Allow All
7️⃣ Configure Wazuh Agent to Read Suricata Logs
Switch to root:

bash
Copy code
sudo -i
cd /var/ossec/etc
sudo nano ossec.conf
Add the following section inside <ossec_config>:

xml
Copy code
<localfile>
  <log_format>json</log_format>
  <location>/var/log/suricata/eve.json</location>
</localfile>
Save and restart Wazuh agent:

bash
Copy code
systemctl restart wazuh-agent
8️⃣ Verify Logs in Wazuh Dashboard
Open the Wazuh web interface and navigate to:

nginx
Copy code
Modules → NIDS → Security Events
You should see alerts such as:

Suricata: Alert - STREAM excessive retransmissions

ET SCAN Potential VNC Scan

ET SCAN Suspicious inbound to SQL ports

