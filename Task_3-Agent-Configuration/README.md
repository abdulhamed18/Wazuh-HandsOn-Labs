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
`Figure 1: Wazuh dashboard – Agent management section`

---

### Step 2: Select Endpoint Operating System
From the agent deployment page:
- Select the desired operating system (Windows / Linux)
- Enter the Wazuh server IP address
- Copy the generated installation command

This command is unique for each environment.

📸 **Screenshot:**  
`Figure 2: Agent deployment configuration for selected OS`

---

### Step 3: Install Wazuh Agent on Endpoint
For a Windows endpoint:
- Open **PowerShell as Administrator**
- Paste and run the generated installation command

```powershell
Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.14.2-1.msi -OutFile $env:tmp\wazuh-agent; msiexec.exe /i $env:tmp\wazuh-agent /q WAZUH_MANAGER='192.168.x.x'
```
