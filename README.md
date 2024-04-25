<p align="center"><img src="https://github.com/shoganaich/azure-network-traffic/assets/112911007/e1b63531-1bbe-4d75-9f4f-320f98df52b4" alt="Traffic Examination"/></p>

# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines
We will use Wireshark to observe network traffic between Azure Virtual Machines and experiment with Network Security Groups.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machine Deployment)
- Wireshark (Packet Analyzer)
- RDP
- Various Command-Line Tools
- Various Network Protocols (ICMP, SSH, DHCP, HTTP/S, etc.)

## Operating Systems Used
- Windows 10 (21H2)
- Ubuntu Server 20.04

## High-Level Steps
- Deploying the VMs on Azure
- Preparing the Wireshark
- Observing the traffic of different network protocols
- Cleaning up the lab

## Actions and Observations
### 1. Access the Azure Portal
Begin by navigating to the [Azure Portal](https://portal.azure.com).

### 2. Create the Resource Group
Create a resource group named "LAB-Wireshark."

![Resource Group](https://hackmd.io/_uploads/S1lPY0D-R.png)

### 3. Create Two Virtual Machines
Set up two virtual machines within the resource group:
- Windows VM (Private IP: 10.0.0.4)
- Ubuntu VM (Private IP: 10.0.0.5)

![Windows VM](https://hackmd.io/_uploads/Hk0gcAvW0.png)
![Ubuntu VM](https://hackmd.io/_uploads/Hk0gcAvW0.png)

### 4. Virtual Network Configuration
Both virtual machines should be created within the same Virtual Network (VNet).

![VNet Configuration 1](https://hackmd.io/_uploads/SyUj5APbA.png)
![VNet Configuration 2](https://hackmd.io/_uploads/Sy1boCDbR.png)

### 5. Remote Desktop Connection
Connect to the Windows VM using Remote Desktop Protocol (RDP).

![RDP Connection](https://hackmd.io/_uploads/Skj6oAP-R.png)

### 6. Install Wireshark
Download and install Wireshark on the Windows VM.

![Wireshark Download](https://hackmd.io/_uploads/SJexh0DW0.png)
![Wireshark Installation](https://hackmd.io/_uploads/BkUlhAD-C.png)

### 7. Monitor ICMP Traffic
#### 7a. Ping Ubuntu VM
Test the connectivity by pinging the Ubuntu VM and observe the ICMP traffic.

![Ping Ubuntu VM](https://hackmd.io/_uploads/SyR-a0wWA.png)

#### 7b. Ping Google.com
Check the connectivity with `google.com`.

![Ping Google.com](https://hackmd.io/_uploads/r1Vjp0PWC.png)

#### 7c. Continuous Ping
Initiate a continuous ping between both VMs.

![Continuous Ping](https://hackmd.io/_uploads/r1iCpCvZ0.png)

#### 7d. Block ICMP Traffic
Create an inbound rule in the Network Security Group to block all ICMP traffic.

![Block ICMP 1](https://hackmd.io/_uploads/H108C0PWA.png)
![Block ICMP 2](https://hackmd.io/_uploads/HJrH0AwWR.png)

#### 7e. Observe Blocked Traffic
Notice that all ICMP traffic between the machines is blocked.

![ICMP Blocked](https://hackmd.io/_uploads/rk5MJJOb0.png)

#### 7f. Delete Rule
After removing the rule, observe the restoration of normal traffic flow.

![Rule Deletion](https://hackmd.io/_uploads/ryjDkJdb0.png)

### 8. SSH Traffic Monitoring
#### 8a. Initiate SSH Connection
Start an SSH session between the Windows VM and the Ubuntu VM, and observe SSH traffic.

![SSH Session](https://hackmd.io/_uploads/HysPe1_ZR.png)

#### 8b. Monitor Commands
Observe the requests and replies with each command typed in the terminal.

![SSH Commands](https://hackmd.io/_uploads/H1Jag1dWA.png)

### 9. Inspect DHCP Traffic
Type the command `ipconfig /renew` on the Windows VM to request a new IP address from the DHCP server, and monitor the DHCP traffic.

![DHCP Traffic](https://hackmd.io/_uploads/rkb6-1u-A.png)

### 10. RDP Traffic Analysis
Inspect the RDP session traffic, which shows a continuous flow as the session remained active throughout the lab. Specifically, inspect the **TCP traffic on `port 3389`** to analyze the RDP traffic in detail.


![RDP Traffic](https://hackmd.io/_uploads/H1EBzkdZC.png)

### 11. Cleanup Resources
Delete the entire resource group to prevent unnecessary costs after the lab is complete.

![Delete Resource Group](https://hackmd.io/_uploads/rJoqMyd-A.png)


## Conclusion and Next Steps

This lab demonstrates network traffic setup and monitoring within an Azure environment using Wireshark. By following these steps, you have learned how to create virtual machines, configure a virtual network, and analyze different types of network traffic, including ICMP, SSH, DHCP, and RDP. These exercises are crucial for understanding network behavior and troubleshooting issues.

I highly recommend that you take a deeper dive into this topic by tweaking the network settings, trying out different types of traffic, and utilizing additional monitoring tools. This will not only improve your comprehension of network management and security but also spark your curiosity and drive to explore further.

Thank you for experiencing this lab. If you have questions or would like to explore more advanced scenarios, please reach out through the issues section of this repository or submit pull requests with your suggestions to improve this lab.

[![hackmd-github-sync-badge](https://hackmd.io/TAcpUkfrToK22Clc0_GfjQ/badge)](https://hackmd.io/TAcpUkfrToK22Clc0_GfjQ)