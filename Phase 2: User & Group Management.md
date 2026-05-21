<p align="center">
  <img src="AD%20Screenshots/MS%20Active%20Directory%20Logo.png" alt="MS Active Directory Logo" width="600" height="600">
</p>

# Phase 2: User & Group Management
This phase demonstrates how New Users and Departments are implemented in Active Directory for a fictitious department store by the name of Shopper's Rite LLC, the domain: helpdesklabs.local

<p align="center">
  <img src="AD Screenshots/ShoppersRite Logo.png" alt="Shopper's Rite Logo" width="300" height="300">
</p>

## Environments & Technologies
- Oracle VirtualBox
- Active Directory Domain Services (AD DS)

## Operating System
- Windows Server 2022 (21H2) | Build 20348.587

## Organizational Unit Separation

![AD Center Overview](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/493dfd304f0609663550dfd45513f78bca2f9c18/AD%20Screenshots/AD%20Center%20Overview.png)

Using the Active Directory Administrative Center, a new Organizational Unit was created for the departments: "ShopRite Group" to ensure a clear structure for the users, departments, and devices of ShopRite LLC [*Right-Click on DC > New >  Organizational Unit*]

![Org Unit](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/493dfd304f0609663550dfd45513f78bca2f9c18/AD%20Screenshots/Org%20Unit.png)

![shopritegroup](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/493dfd304f0609663550dfd45513f78bca2f9c18/AD%20Screenshots/shopritegroup.png)


## User and Security Group Creation

A total of 20 staff members and 6 groups were added to the ShopRite Group organizational unit.

- New Group Name: IT_Users
- Group Type: *Security* - to ensure that the assigned users will have permissions to the shared resources on the helpdesklabs domain.
- Group Scope: *Global* -  to grant access to team-specific resources to users.
- Enabled: *Protect from accidental deletion*

![IT_Users Group](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/493dfd304f0609663550dfd45513f78bca2f9c18/AD%20Screenshots/IT_Users%20Group.png)

![Group Listing](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/493dfd304f0609663550dfd45513f78bca2f9c18/AD%20Screenshots/Group%20Listing.png)

The first user created was Daniel Moore, the IT Manager. The following settings were applied to this AD account:

- New User: Daniel Moore
- Username: dmoore
- Department:  IT Support Team
- Job Title: IT Manager
- Temp Password: **********
- Enabled: *Protect from accidental deletion*

![New User dmoore](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/9ec7839ec770a0d7cc4d34ae3aefabbb9cd4b9c3/AD%20Screenshots/New%20User%20dmoore.png)

This user was assigned to the following groups: IT_Users, Domain Users (added automatically)
[*Member of > Enter object "IT_Users" > Check Names > OK* ]

![check names](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/9ec7839ec770a0d7cc4d34ae3aefabbb9cd4b9c3/AD%20Screenshots/check%20names.png)

![dmoore groups](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/9ec7839ec770a0d7cc4d34ae3aefabbb9cd4b9c3/AD%20Screenshots/dmoore%20groups.png)

![Users List](https://github.com/KelsACzr/User-Group-Management-Active-Directory-/blob/9ec7839ec770a0d7cc4d34ae3aefabbb9cd4b9c3/AD%20Screenshots/Users%20List.png)

In the final phase of this lab, I explore Group Policy, Access Management, and Common Tasks done in Active Directory by a Technical Support Specialist.



















