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

![01](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/42d61ba7-583c-4e2b-8432-cb92abb5f574)

### 3. Create Two Virtual Machines
Set up two virtual machines within the resource group:
- Windows VM (Private IP: 10.0.0.4)
- Ubuntu VM (Private IP: 10.0.0.5)

![02](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/0684db12-2a11-4f9c-84d6-a249c5cb445d)

### 4. Virtual Network Configuration
Both virtual machines should be created within the same Virtual Network (VNet).

![03](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/7fd05a16-c0c5-40f0-a91f-e6328d64ad8d)
![04](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/01c2fe50-28df-4a4b-94e8-184eb5dfb914)

### 5. Remote Desktop Connection
Connect to the Windows VM using Remote Desktop Protocol (RDP).

![05](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/bbb1b3ec-da5b-429a-902d-93746f2ff7f2)

### 6. Install Wireshark
Download and install Wireshark on the Windows VM.

![06](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/3bb38ecc-9ec6-4bc8-8222-ec4a7a06d917)
![07](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/106fc7d9-8a75-4654-860e-b4c8acf4a6cd)

### 7. Monitor ICMP Traffic
#### 7a. Ping Ubuntu VM
Test the connectivity by pinging the Ubuntu VM and observe the ICMP traffic.

![08](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/83587995-5adf-451e-a2a3-a640ecc63a53)

#### 7b. Ping Google.com
Check the connectivity with `google.com`.

![09](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/47f33484-a31d-4acc-a9b0-0f512ed972b1)

#### 7c. Continuous Ping
Initiate a continuous ping between both VMs.

![10](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/3b63141f-b5c5-495e-8211-486fcc4913dc)

#### 7d. Block ICMP Traffic
Create an inbound rule in the Network Security Group to block all ICMP traffic.

![11](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/b8847b6b-6174-4590-bf9d-f22ba84124aa)
![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/c52835bb-c30c-4fa7-87ec-b55148f25d70)

#### 7e. Observe Blocked Traffic
Notice that all ICMP traffic between the machines is blocked.

![13](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/044194fc-4d4f-4952-86da-e8e754db4361)

#### 7f. Delete Rule
After removing the rule, observe the restoration of normal traffic flow.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/28419d7c-33c0-4bd0-92d2-73c9d23d0568)

### 8. SSH Traffic Monitoring
#### 8a. Initiate SSH Connection
Start an SSH session between the Windows VM and the Ubuntu VM, and observe SSH traffic.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/3df8c39b-782f-4a31-b455-8baf357965cf)

#### 8b. Monitor Commands
Observe the requests and replies with each command typed in the terminal.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/50604bcf-8139-4694-8cd0-c3b4788e40a2)

### 9. Inspect DHCP Traffic
Type the command `ipconfig /renew` on the Windows VM to request a new IP address from the DHCP server, and monitor the DHCP traffic.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/523cfb78-1a08-49da-84ec-d60d9a4b188e)

### 10. RDP Traffic Analysis
Inspect the RDP session traffic, which shows a continuous flow as the session remained active throughout the lab. Specifically, inspect the **TCP traffic on `port 3389`** to analyze the RDP traffic in detail.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/517ad807-325b-4778-b167-72735a9a2688)

### 11. Cleanup Resources
Delete the entire resource group to prevent unnecessary costs after the lab is complete.

![image](https://github.com/shoganaich/azure-traffic-inspect/assets/112911007/86923081-a824-464d-81d6-853b67ddd6c4)

## Conclusion and Next Steps

This lab demonstrates network traffic setup and monitoring within an Azure environment using Wireshark. By following these steps, you have learned how to create virtual machines, configure a virtual network, and analyze different types of network traffic, including ICMP, SSH, DHCP, and RDP. These exercises are crucial for understanding network behavior and troubleshooting issues.

I highly recommend that you take a deeper dive into this topic by tweaking the network settings, trying out different types of traffic, and utilizing additional monitoring tools. This will not only improve your comprehension of network management and security but also spark your curiosity and drive to explore further.

Thank you for experiencing this lab. If you have questions or would like to explore more advanced scenarios, please reach out through the issues section of this repository or submit pull requests with your suggestions to improve this lab.

<!-- LICENSE -->
## License
Distributed under the MIT License. See `LICENSE` for more information.

## Acknowledgments
* [osTicket](https://osticket.com/)
* [Course Carrers](https://coursecareers.com/)
* [Josh Madakor](https://www.linkedin.com/in/joshmadakor)

[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://www.github.com/shoganaich/)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/victordccardoso/)
[![linkedin](https://img.shields.io/badge/telegram-fbfcf8?style=for-the-badge&logo=telegram&logoColor=blue)](https://t.me/shoganaich)
