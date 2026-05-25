<p align="center">
  <img src="AD%20Screenshots/MS%20Active%20Directory%20Logo.png" alt="MS Active Directory Logo" width="600" height="600">
</p>

# Phase 3: Group Policy, Access Management, and Common Tasks
 
 This phase demonstrates the application of Group Policy Objects (GPOs) in Active Directory for a fictitious department store by the name of Shopper's Rite LLC on the Domain Controller (DC): helpdesklabs.
 
 ## Environments & Technologies
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)
- Group Policy (GPO)

## Operating System
- Windows Server 2022 (21H2) | Build 20348.587

## Group Policy Objects (GPOs) Creation

The following GPOs were created on Domain Name: helpdesklabs.

[*Server Manager >  Tools > Group Policy Management*]

![GPO Management](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/36bc99abfb8a9906a1ad47bce403e073c4ed258b/AD%20Screenshots/GPO%20Management.png)

![GPO helpdesklabs](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/36bc99abfb8a9906a1ad47bce403e073c4ed258b/AD%20Screenshots/GPO%20helpdesklabs.png)

GPOs 1-4 were applied to the *Account Policies* under *Computer Configuration*.

[*Edit Default Domain Policy > Computer Configuration > Policies >  Windows Settings > Security Settings > Account Policies*]


![Account Policies](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/5c27a3f94269651ebae74c5918e07af50a30d3c7/AD%20Screenshots/Account%20Policies.png)


**1. Password Policy**

The user would be required to create a password of at least 10 characters, with complexity enabled and a 90-day expiry. 

![Password Policy Settings](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/5c27a3f94269651ebae74c5918e07af50a30d3c7/AD%20Screenshots/Password%20Policy%20Settings.png)


**2. Account Lockout Policy**
The user would be locked out after 5 failed attempts and unlocked after 30 minutes.

![Lockout Policy Settings](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/b0812a6ad11be36aff8f3b7118c3470bf96191d7/AD%20Screenshots/Lockout%20Policy%20Settings.png)

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)


**3. USB Storage Restriction for non-IT users.**

The average user would not be able to insert and utilize removable storage devices to prevent replication of sensitive company data.

![USB Policy Settings](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/b0812a6ad11be36aff8f3b7118c3470bf96191d7/AD%20Screenshots/USB%20Policy%20Settings.png)

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)


**4. Login Banner displaying authorized use warning.**

This policy was applied under the *Security Options* of the *Local Policies*. The users would be greeted with the following message as a reminder of the company's IT Security policies

Title: Shopper's Rite LLC IT Security Notice

Message:
"This system is the property of Shopper's Rite LLC and is intended for authorized use only. All access and activity may be monitored, recorded, and audited. Unauthorized use is prohibited and may result in disciplinary or legal action."

![Security Notice Setting](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/b0812a6ad11be36aff8f3b7118c3470bf96191d7/AD%20Screenshots/Security%20Notice%20Setting.png)

![Security Banner Confirmed](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/b0812a6ad11be36aff8f3b7118c3470bf96191d7/AD%20Screenshots/Security%20Banner%20Confirmed.png)


**5. Mapped Network Drive: The Sales department got access to a shared network drive.**

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)

**6. Desktop Wallpaper Policy - TO COMPLETE**
This GPO applies the company logo as the wallpaper on all workstations.

![Wallpaper Setting](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)


GPOs 7-8 were applied to the *Account Policies* under *User Configuration*.

[*Edit Default Domain Policy > User Configuration > Policies >  Windows Settings > Security Settings > Account Policies*]


7. Disable Control Panel
The control panel would be disabled for non-members of the IT_Users Group. This requires the creation of a new GPO named "Control Panel Lock for Non-IT Users."

[*GPO Management > Domains > helpdesklabs.local > Right-Click + Group Policy Objects > New*]

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)

8. Auto Screen Lock 

The user's workstation will lock after 5–10 minutes (600 seconds) of inactivity for the purpose of privacy.

![Auto Screen Lock Settings](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/27f1592b4138694cbb75e9b0ca887e863697505d/AD%20Screenshots/Auto%20Screen%20Lock%20Settings.png)

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)



## Common Active Directory Tasks

Here are some of the most common Active Directory scenarios you may face while working in a Technical Support Environment;

Issue: User Locked out of their Domain Login
Possible Cause: The user has entered the incorrect password multiple times, or their password has expired after they have spent a significant amount of time offline. i.e., during vacation or a leave of absence.
Solution:
- Confirm the User's Full Name and Log-On Username
- Go to Active Directory > 

  ![User View Lockout](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)
  
- Password Reset
  - This may be requested by the user
- Grant access by adding a user to the correct security group.
- Onboard a new employee (create user, assign OU, and group).
- Disable an account for a terminated employee.
- Transfer a user between departments and update permissions.
- Troubleshoot a login/profile issue.
- Restrict or grant access to shared resources using groups

