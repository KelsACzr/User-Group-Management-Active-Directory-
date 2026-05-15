<p align="center">
  <img src="AD%20Screenshots/MS%20Active%20Directory%20Logo.png" alt="MS Active Directory Logo">
</p>

# Phase 1: Infrasructure Setup
This section explains the required prerequisites and installation process for setting up the Active Direcory on a Windows Server. Active Directory would be used to manage the Users, Computers and Policies required for the operations of a ficticious company called Shopper's Rite LLC. 

## Environments & Technologies
- Oracle VirtualBox
- Internet Information Services (IIS)

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
	- Test Domain User Creation
	
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
Server Manager > Local server > Click Computer Name > Under Computer Name Tab > Set Compter Description >  Select Change > Set Computer Name > OK > Reboot Server.

New Server Machine Name: VMSERVER

### Domain Creation & Server Promotion to Domain Controller

### Active Directory Domain Services and DHCP Server Installation

Active Directory Domain Servies and the DHCP Server were installed via the Server Manager Server roles. 

Go to: Server Manager > Manage > Add Roles and Features > Select: Active Direcory Domain Services & DHCP Server

![DHCP and AD Server Roles Install](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/5d4bf2e85b22576710318739bc3ae1a22994a4d5/AD%20Screenshots/DHCP%20and%20AD%20Server%20Roles%20Install.png)

### DHCP Server Configuration

The DHCP Server is responsible for managing and delegating IP addresses to the workstations connected to the domain: helpdesklabs.local the DHCP Server needed to be added to the list of authorized DHCP servers in Active Directory via PowerShell.

[*Add-DhcpServerInDC -DnsName SRLLC_DHCP1 -IPAddress 192.168.10.0*]

- DNS Name: SRLLC_DHCP1
- Network Address:	192.168.10.0

![DHCP Server Auth](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/f5f4aeb800a5b65efbe5343ded71a3b94351e869/AD%20Screenshots/DHCP%20Server%20Auth.png)

The authorization was then confirmed. [*Get-DhcpServerInDC*]

![DHCP Server Auth Confirmation](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/f5f4aeb800a5b65efbe5343ded71a3b94351e869/AD%20Screenshots/DHCP%20Server%20Auth%20Confirmation.png)

Next, the host range was configured. [*Add-DhcpServerv4Scope -Name "SRLLC Network" -StartRange 192.168.10.1 -EndRange 192.168.10.254 -SubnetMask 255.255.255.0*]

Usable Host IP Range: 192.168.10.1 - 192.168.10.254
Subnet Mask: 255.255.255.0
