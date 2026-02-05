# Task 3 – Agent Installation & Configuration

After completing the Wazuh server installation and getting access to the Wazuh dashboard, the next step is to install and configure the Wazuh agent on an endpoint system.

---

### Step 1: Access Agent Management in Wazuh Dashboard
Log in to the Wazuh dashboard using the administrator credentials.

Navigate to:
- **Agents Management → Summary**
- Click on **Deploy new agent**

This section allows us to generate agent installation commands based on the selected operating system.

<img width="1757" height="703" alt="image" src="https://github.com/user-attachments/assets/923ec546-9829-476d-8733-04834dfd768c" />
Figure 1: Wazuh dashboard – Agent management section

---

### Step 2: Select Endpoint Operating System
From the agent deployment page:
- Select the desired operating system (Windows / Linux)
- Enter the Wazuh server IP address
- Copy the generated installation command

This command is unique for each environment.

---

### Step 3: Install Wazuh Agent on Endpoint
#### For a Windows endpoint:
- Open **PowerShell as Administrator**
- Paste and run the generated installation command

```powershell
Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.14.2-1.msi -OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent /q WAZUH_MANAGER='<WAZUH_SERVER_IP>'
```

   #### For a Linux(debian) endpoint:
   - Open **Terminal as Super User**
   - Paste and run the generated installation command

```bash
wget https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.14.2-1_amd64.deb && sudo WAZUH_MANAGER='<WAZUH_SERVER_IP>' dpkg -i ./wazuh-agent_4.14.2-1_amd64.deb
```
- This command downloads and installs the Wazuh agent on the Endpoint system.

---

### Step 4: Start the Wazuh Agent Service

After installation, the Wazuh agent service must be started.
#### For Windows:
```powershell
NET START Wazuh
```

#### For Linux:
```bash
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```
- Once started, the agent begins communicating with the Wazuh server.

---

### Step 5: Verify Agent Connection in Dashboard

- Return to the Wazuh dashboard and refresh the Agents section.
- The agent status should appear as **Active**
- Agent details such as name, IP, and OS should be visible

<img width="1813" height="728" alt="image" src="https://github.com/user-attachments/assets/f125c18d-1d71-45e8-ab63-603b21e2cd47" /> 
Figure 2: Agent successfully connected and active in dashboard

### If Agent is Not Showing as Active (Troubleshooting)

If the agent does not appear as **Active**, the following checks can be performed:


1. **Check Agent Service Status**
   Make sure the Wazuh agent service is running.  
   If needed, restart the service.

   **Windows:**
   ```powershell
   NET STOP Wazuh
   NET START Wazuh
   ```

   **Linux:**
   ```bash
   sudo systemctl restart wazuh-agent
   ```

---

2. **Verify Wazuh Manager IP**
  - Confirm that the correct Wazuh server IP is configured in the agent settings.

   **Linux:**
   Check the manager address in:
   ```bash
   /var/ossec/etc/ossec.conf
   ```

   **Windows:**
   Check the manager address in:
   ```
   C:\Program Files (x86)\ossec-agent\ossec.conf
   ```
   - An incorrect server IP will prevent the agent from connecting.

---

3. **Network Connectivity Check**
   Verify that the endpoint can reach the Wazuh server over the network.
      ```bash
      ping <WAZUH_SERVER_IP>
      ```
      - If the ping fails, check network configuration and firewall rules.

After fixing these issues, refresh the Wazuh dashboard and verify that the agent status changes to **Active**.



