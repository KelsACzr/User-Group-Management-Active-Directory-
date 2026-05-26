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

The user's workstation will lock after 5–10 minutes (600 seconds) of inactivity to protect privacy.

![Auto Screen Lock Settings](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/27f1592b4138694cbb75e9b0ca887e863697505d/AD%20Screenshots/Auto%20Screen%20Lock%20Settings.png)

![GPO TEST CONFIRMATION](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)



## Common Active Directory Tasks

Here are some of the most common Active Directory scenarios you may face while working in a Technical Support Environment;


**New Employee Onboarding**

As part of the onboarding process, new employees need to have their domain credentials created and provided to them before or upon their assumption of duty. Such a request should be sent to the helpdesk by a company's HR team with the following details;
	
	- Full Name: Alena Jefferson-Clarke
	- Position: Payroll Clerk II
	- Department: Finance
	- Supervisor: Ryan Ali
	- OU: SRLLC_Users
	- Groups: Finance_Users, SRLLC_All_Users
	
To create a new user, right-click on the Organizational Unit the user should be assigned to > Click "New" > Click "User"
	
![New User Create](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)
	
Next, the User Object details are entered as follows: First Name, Last Name, User Log-On Name > Click "Next"
	
_User Log-On names should only contain alphanumeric characters and not contain spaces or special characters. Example: ajclarke_
	
Enter a Temporary Password for the user to log in for the first time. They would be prompted to change their password upon their first login > Click "Finish"
	
_Passwords must be compliant with the GPO Password Policy as shown above_
	
The user must then be added to the relevant AD Groups i.e., Finance_Users, SRLLC_All_Users, using the steps mentioned above.


**User Locked out of their Domain Login**

This can occur when a user has entered the incorrect password multiple times, or their password has expired after they have spent a significant amount of time offline. i.e., during vacation or a leave of absence.

![User View Lockout](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)

To alleviate this, the user's account needs to be unlocked, and their password needs to be reset as follows;

Unlock the user's account in Active Directory:
	- Confirm the User's Full Name and Log-On Username
	- Go to Active Directory > Go to the toolbar below the menu > Click the "Find Objects in Active Directory Domain Services" icon. 

	![Find Objects in AD Icon](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)

	- Change the **In** field to "Entire Directory" > Enter the Username into the **Name** field > Click Find Now.
	- Once the search results populate in the window below: Double-click the User's Name > Click the **Account Tab** > Check **Unlock Account** > Click OK
	- Have the user attempt to log in and confirm that they were able to log in.
	
Reset the user's password:
	- Search for the User's Name or Log-On username using the steps above. 
	-
  
**Restrict or Grant access through Security Groups**
In some cases, a user may be unable to access a domain resource as a result of their AD account not being a member of an Active Directory Security Group. There may also be a case where the user is switching departments and needs access to the resources of their new team.
	
To add the user to the respective security group. Example: SRLLC_All_Users 
	- Confirm the Full Name and AD Log-On with the user
	- Search for the user using the steps above.
	- Click the "Member Of" tab > Click "Add" > Go to "Enter the object names to select "Enter the Group Name "SRLLC_All_Users" > Click "Check Names" > Click OK > Click Apply 		> Click OK
		
	_Once the group name object is underlined, this means that the group is selected _
		
	![Add to Sec Group](AD%20Screenshots/MS%20Active%20Directory%20Logo.png)
		
	- To revoke access, the group name is removed from the user's list on the "Member Of" tab: Select the Group Name > Click "Remove" > Click Apply and OK.

	
**Active Directory Account Termination**
The request to terminate an employee's domain account should be sent to the helpdesk by the company's HR Team. This includes;	

- Disabling the User's account: Search the AD account by the Log-on Username > Click the "Account" tab >

- Resetting the Password using the steps shown above.
		
_The account/data should not be deleted as the contents may be needed for a company's records._

