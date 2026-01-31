# Task 1 – What is Wazuh

## Objective
The goal of this task is to understand what Wazuh is, how it operates, and what components it uses before starting practical labs.

---

## What is Wazuh?

Wazuh is an open-source security platform that combines **SIEM (Security Information and Event Management)** and **XDR (Extended Detection and Response)** capabilities.

It is mainly used to improve system security by:
- Monitoring operating systems and applications  
- Collecting and analyzing log data  
- Detecting suspicious and malicious activity  
- Tracking file changes  
- Finding vulnerable software  
- Taking automatic actions when attacks are detected  

Wazuh can be used in both enterprise networks and small home lab environments.

---

## How Wazuh Works (High-Level View)

Wazuh works using a client-server architecture:

1. A **Wazuh agent** is installed on each monitored system such as Linux or Windows.
2. The agent collects logs and security-related events from the system.
3. These logs are sent securely to the **Wazuh manager**.
4. The manager processes the data using decoders and detection rules.
5. When abnormal behavior is found, security alerts are created.
6. All collected data is stored in the indexer and displayed in the dashboard.

---

## Main Components of Wazuh

### 1. Wazuh Agent
- Runs on endpoint systems (Linux or Windows).
- Gathers logs and security information.
- Sends collected data to the Wazuh manager for analysis.

---

### 2. Wazuh Manager (Server)
- Acts as the core of the Wazuh system.
- Receives logs from agents.
- Applies rules to detect threats.
- Generates alerts when suspicious activity is identified.

---

### 3. Indexer
- Used to store and organize security data.
- Supports fast searching and log analysis.
- Keeps alert data for later investigation.

---

### 4. Dashboard
- A web-based interface for users.
- Shows alerts, logs, and system status.
- Helps security analysts monitor and investigate incidents.

---

## Main Capabilities of Wazuh

- Log monitoring and analysis  
- File Integrity Monitoring (FIM)  
- Vulnerability scanning  
- Rootkit and malware detection  
- Automated response actions  
- Compliance and audit support  
- Threat and intrusion detection  

---

## Example Scenario

If an attacker attempts to log in repeatedly using wrong SSH passwords:

1. The agent records the failed login attempts.
2. The manager analyzes these records.
3. Detection rules identify the activity as a brute-force attack.
4. A security alert is generated.
5. An automatic response can block the attacker’s IP address.

---

## Learning Outcome

From this task, I learned:
- The purpose of Wazuh and where it is used  
- The basic working model of Wazuh  
- The role of each main component  
- How Wazuh helps in detecting security threats  

---

## References
- Wazuh Documentation: https://documentation.wazuh.com/current/quickstart.md
