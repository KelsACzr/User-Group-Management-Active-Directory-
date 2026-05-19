<p align="center">
  <img src="AD%20Screenshots/MS%20Active%20Directory%20Logo.png" alt="MS Active Directory Logo">
</p>

# Phase 1: Infrastructure Setup
This section explains the required prerequisites and installation process for setting up the Active Directory on a Windows Server. Active Directory would be used to manage the users, computers, and Policies required for the operations of a fictitious company called Shopper's Rite LLC. 

## Environments & Technologies
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- Group Policy (GPO)

## Operating System
- Windows Server 2022 (21H2) | Build 20348.587
- Windows 10 Pro (22H2) |  Build 19045.4529

## List of Prerequisites

*Note: The Virtual Machine's network adapter settings must be set to "Internal Network" for the Server and Client machines.*
![network adapter set](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/90c8a37bef31f24c27c3295981e2c14831b95402/AD%20Screenshots/network%20adapter%20set.png)

- Win Server 2022 VM Configuration
  	- Set static IP for the Server Machine
  	- Rename Server Machine
  	- Domain Creation & Server Promotion to Domain Controller
	- Active Directory Domain Services and DHCP Server Installation
	- DHCP Server Configuration
	
- Client VM Configuration
	- Install Win 10 Pro OS
	- Rename Workstation
	- Add Workstation to the Domain

## 1. Windows Server 2022 Configuration

### Set Static IP for the Server Machine
In the previous lab, the server would have used an IP address set by DHCP.  For this lab, the IP address was set to static. 

Control Panel > Network and Sharing Center > Change Adaper Settings > Right-click on Ethernet > Properties > Internet Protocol Version 4 (TCP IPv4) > General > Use the Following IP Address > OK

- IPv4 Address: 192.168.10.10
- Subnet Mask: 255.255.255.0
- Preferred DNS: 192.168.10.10

![Server Static IP address set](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/fc15378360f2a26ac2c8791fd1b0c435f9d58116/AD%20Screenshots/Server%20Static%20IP%20address%20set.png)

### Rename Server Machine
Server Manager > Local server > Click Computer Name > Under Computer Name Tab > Set Computer Description >  Select Change > Set Computer Name > OK > Reboot Server.

New Server Machine Name: VMSERVER

### Domain Creation & Server Promotion to Domain Controller

The following Domain was created and promoted to a domain controller. 

Domain Name: helpdesklabs.local

![Promote Domain Controller and New Forrest Creation](image url .png)


The domain was successfully created and confirmed via PowerShell: GET-ADFOREST 

![Domain setup successful 2](image url .png)
![Domain Controller Set](image url .png)


![domain setup successful](image url .png)


### Active Directory Domain Services and DHCP Server Installation

Active Directory Domain Services and the DHCP Server were installed via the Server Manager roles. 

Go to: Server Manager > Manage > Add Roles and Features > Select: Active Directory Domain Services & DHCP Server

![AD Center Overview](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/be383c9a8f583ecc812f51396b5d347d8c25d609/AD%20Screenshots/AD%20Center%20Overview.png)

![DHCP and AD Server Roles Install](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/5d4bf2e85b22576710318739bc3ae1a22994a4d5/AD%20Screenshots/DHCP%20and%20AD%20Server%20Roles%20Install.png)

- AD Server Role:
	- Installation Type: "Role-based or feature-based installation."
	- Server Selection:  VMSERVER.helpdesklabs.Local
	- Server Roles: Active Directory Domain Services

### DHCP Server Configuration

The DHCP Server is responsible for managing and delegating IP addresses to the workstations connected to the domain: helpdesklabs.local. The DHCP Server needed to be added to the list of authorized DHCP servers in Active Directory via PowerShell.

[*Add-DhcpServerInDC -DnsName SRLLC_DHCP1 -IPAddress 192.168.10.0*]

- DNS Name: SRLLC_DHCP1
- Network Address:	192.168.10.0

![DHCP Server Auth](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/f5f4aeb800a5b65efbe5343ded71a3b94351e869/AD%20Screenshots/DHCP%20Server%20Auth.png)

The authorization was then confirmed. [*Get-DhcpServerInDC*]

![DHCP Server Auth Confirmation](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/f5f4aeb800a5b65efbe5343ded71a3b94351e869/AD%20Screenshots/DHCP%20Server%20Auth%20Confirmation.png)

Next, the host range was configured. [*Add-DhcpServerv4Scope -Name "SRLLC Network" -StartRange 192.168.10.1 -EndRange 192.168.10.254 -SubnetMask 255.255.255.0*]

- Usable Host IP Range: 192.168.10.1 - 192.168.10.254
- Subnet Mask: 255.255.255.0

*A new user with admin privileges was created. We would go into user creation in detail in the subsequent phases.*

## 2. Client VM Configuration

- Installed Windows 10 Pro (22H2) | Build 19045.4529 and ran system updates

- Renamed Workstation to match the company naming convention:
	- Workstation Name: VMCLIENT01
	- Username: srllcadmin
	- Password: ***********

![Windows 10 Enterprise Install](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/60906aa25c5e309d044716d092637e5e6d048aef/AD%20Screenshots/Windows%2010%20Pro%20Install.png)

### Adding the Client Workstation to the Domain

The Workstation: VMCLIENT01 was added to the Domain: helpdesklabs using the system settings.

[*System Settings > System > About > Rename this PC (advanced) > Computer Name Tab > Change > Domain > Enter Domain Name > OK > Apply + OK *]

![enter domain name](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/4b38cfe198f14ef9f6f2d3ce36c765a36c7f852c/AD%20Screenshots/enter%20domain%20name.png)

![domain add successful]

Once the workstation was rebooted, the login to the domain was tested. *A demo user was created for the client machine. The user creation process was detailed in Phase 2: User & Group Management.*

- User Logon Name: dmoore
- Name: Daniel Moore
- Role: IT Manager
- Department: IT Support

![domain login successful]


