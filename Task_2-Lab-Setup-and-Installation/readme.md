# Task 2 – Lab Setup and Installation

## Objective
The objective of this task is to set up a basic lab environment and install the Wazuh server and agent for hands-on practice.  

---

## Lab Environment
This lab is built using virtual machines to simulate a small network environment.  
It includes:
- VirtualBox as the virtualization platform  
- Ubuntu 22.04.5 running the Wazuh server (manager, indexer, and dashboard)  
- Other machines acting as endpoints with the Wazuh agent installed  

All machines are connected to the same virtual network so they can communicate with each other.  
In my case, I created a custom NAT network for all machines.

The lab is designed to be simple and suitable for learning and testing the security features of Wazuh.

---

## System Requirements
The following minimum requirements are used for this lab:
- At least 4 GB RAM for the server  
- At least 2 CPU cores for the server  
- Stable network connectivity between machines  

These resources are sufficient for a small learning lab environment.

---

## Installation Method
According to the official Wazuh documentation, there are two main installation methods:
- **Step-by-step manual installation**
- **Assisted installation (installation script)**

Another option is to deploy the prebuilt **Wazuh .ova virtual machine** directly in VirtualBox.

For this lab, I chose the **assisted installation method** because it is faster and easier for a learning environment.

---

## Wazuh Server Installation

### Prerequisites
Before starting the installation:
- The system was updated
- `curl` was installed on the server

### Assisted Installation Steps

1. Download the Wazuh installation script:
```
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
```
2. Give execution permission to the script:
```
sudo chmod +x wazuh-install.sh
```
3. Run the assisted installation:
```
sudo ./wazuh-install.sh -a
```
#### Note

- After running third command the installer displays the dashboard URL, username, and password.
- It is important to save these credentials and also create a backup copy, because they are required to log in to the Wazuh dashboard.

---

## Wazuh Dashboard Access
The Wazuh dashboard can be accessed from a web browser using:
```
https://<WAZUH_SERVER_IP>
````
Login using the username and password provided at the end of the installation process.

---

## Problems Faced
- Accessing the dashboard from the host machine browser was difficult because the lab was using a **NAT network**, which does not allow direct access from host to VM.

To solve this issue, I configured **port forwarding**:
- Wazuh server port `443` was forwarded to host port `8443`.

After this, I was able to access the dashboard from the host browser using:

```
https://127.0.0.1:8443
```

---

## Learning Outcome
From this task, I learned:
- How to set up a basic Wazuh lab environment using virtual machines  
- Different installation methods available for Wazuh  
- How to install Wazuh using the assisted installation script  
- How to access the Wazuh dashboard after installation  
- How to solve access issues using port forwarding in a NAT network  

---

## References
- Wazuh Documentation: https://documentation.wazuh.com  
- Wazuh Installation Guide: https://documentation.wazuh.com/current/quickstart.html 
