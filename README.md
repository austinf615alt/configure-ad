<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This project outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Windows Server Manager
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2025 Datacenter X64 Gen2 (x2 for Client VM and Domain Controller VM)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Install and Configure Active Directory Domain Services (AD DS)
- Step 2: Configure Domain Administrative Accounts and Organizational Units
- Step 3: Join the Client Virtual Machine to the Domain
- Step 4: Create and Manage Domain User Accounts and Verify Domain Authentication

<h2>Deployment and Configuration Steps</h2>

---

## Step 1: Install and Configure Active Directory Domain Services (AD DS)

---

<p>
<img width="1624" height="981" alt="AD-VM RD Info" src="https://github.com/user-attachments/assets/de431542-58bb-4635-afa6-a1e11b540419" />
</p>
<p>
  
- Recorded the public IP address of the Domain-Controller virtual machine to establish a Remote Desktop connection for server configuration.
  
</p>
<br />

<p>
<img width="1624" height="976" alt="AD-VM Add Features" src="https://github.com/user-attachments/assets/429d871c-947b-438d-a982-a3e0d34b08c7" />
</p>
<p>
  
- Connected to the Domain-Controller virtual machine using Remote Desktop and navigated to Add Roles and Features in Server Manager to begin installing Active Directory Domain Services.

</p>
<br />

<p>
<img width="1624" height="976" alt="AD-VM Add DS" src="https://github.com/user-attachments/assets/56477f9f-9817-4a10-b358-0ee15f8da404" />
</p>
<p>
  
- Enabled the Active Directory Domain Services (AD DS) server role, preparing the Windows Server environment for domain controller functionality.

</p>
<br />

<p>
<img width="1624" height="976" alt="AD-VM Install DS" src="https://github.com/user-attachments/assets/9aac03ea-cce7-49aa-874f-bceb63d8805e" />
</p>
<p>
  
- Successfully installed Active Directory Domain Services and its required supporting features, allowing the server to be promoted to a domain controller.

</p>
<br />

<p>
<img width="1624" height="979" alt="AD-VM Add Forest" src="https://github.com/user-attachments/assets/50007a74-1130-4fac-a697-6f46e66487a8" />
</p>
<p>
  
- Promoted the server to a domain controller by creating a new Active Directory forest and configuring the domain name as mydomain.com.

</p>
<br />

<p>
<img width="1624" height="981" alt="AD-VM Promoted" src="https://github.com/user-attachments/assets/a0950fa4-890f-4fd7-925b-14f77ae4a8ac" />
</p>
<p>
  
- Successfully completed domain controller promotion, enabling centralized domain-based authentication and management for client systems.

</p>
<br />

<p>
<img width="1624" height="971" alt="AD-VM Domain Login" src="https://github.com/user-attachments/assets/72bc4528-4187-4222-8ad5-b2d8f3bdbfb6" />

</p>
<p>
  
- Restarted the server and logged in using the domain account mydomain.com\labuser, using whoami in PowerShell to verify successful domain authentication.

</p>
<br />

---

## Step 2: Configure Domain Administrative Accounts and Organizational Units

---

<p>
<img width="1624" height="974" alt="AD-VM ADUC" src="https://github.com/user-attachments/assets/5d507f07-30e7-4ec8-a1b2-69ed61959394" />
</p>
<p>
  
- Opened Active Directory Users and Computers (ADUC) from Server Manager to begin organizing domain users and administrative accounts

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM Create OU" src="https://github.com/user-attachments/assets/c78ee78b-5077-4b2a-9fce-abe83be7a6b7" />
</p>
<p>
  
- Navigated within the domain structure in ADUC to begin creating organizational units for user account organization.

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM OUs Created" src="https://github.com/user-attachments/assets/30a6a0ae-e437-427e-8da1-bb75bbb63488" />
</p>
<p>
  
- Created the _EMPLOYEES and _ADMINS organizational units to separate standard user accounts from administrative accounts for cleaner directory organization.

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM Create User" src="https://github.com/user-attachments/assets/2f25c9d1-a5bf-4d2e-ae44-1a089b6b10de" />
</p>
<p>
  
- Navigated to the _ADMINS organizational unit to create a dedicated administrative user account for domain management.

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM User Created + Properties" src="https://github.com/user-attachments/assets/c61d6bd6-c78b-414d-ba21-2e0a6660e0be" />
</p>
<p>
  
- Created a new domain administrator account for Jane Doe within the administrative organizational unit. Username is jane_admin.

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM Adding Domain Admin" src="https://github.com/user-attachments/assets/f68776e9-ec37-41aa-b042-f2d6dfb7faee" />
</p>
<p>
  
- Added the jane_admin account to the Domain Admins security group to grant full administrative privileges within the domain environment.

</p>
<br />

<p>
<img width="1624" height="974" alt="AD-VM Jane Login" src="https://github.com/user-attachments/assets/3487a747-b2e3-46fb-8a0c-68a925459fe8" />
</p>
<p>
  
- Signed out of the original local domain account (labuser) and successfully logged in using mydomain.com\jane_admin to verify administrative access to the domain.

</p>
<br />

---

## Step 3: Join the Client Virtual Machine to the Domain

---

<p>
<img width="1624" height="976" alt="Client-1 VM Adding Domain" src="https://github.com/user-attachments/assets/61dc0157-5dd0-450d-9c57-7e56d30f79ec" />
</p>
<p>
  
- Connected to the Client-1 virtual machine using Remote Desktop and accessed system settings to join the machine to the mydomain.com domain.

</p>
<br />

<p>
<img width="1624" height="981" alt="Client-1 Domain Auth" src="https://github.com/user-attachments/assets/7bc624ae-f555-4554-aa44-938e3b973875" />
</p>
<p>
  
- Entered domain administrator credentials (mydomain.com\jane_admin) to authorize the client system’s addition to the Active Directory domain.

</p>
<br />

<p>
<img width="1624" height="974" alt="Client-1 Join Verify" src="https://github.com/user-attachments/assets/3ad4d867-8c83-4b92-b042-d204ed45aa9c" />
</p>
<p>
  
- Verified within Active Directory that Client-1 successfully joined the domain, confirming proper domain integration.

</p>
<br />

---

## Step 4: Create and Manage Domain User Accounts and Verify Domain Authentication

---

<p>
<img width="1624" height="979" alt="Client-1 Enabled RD for Non-Admins" src="https://github.com/user-attachments/assets/67fb0845-56f6-4afc-9dc4-01801a0b9f0d" />
</p>
<p>
  
- Configured Client-1 to allow domain users to access the system through Remote Desktop for lab testing and authentication verification.

- Note: In production environments, remote access permissions would be managed more securely through Group Policy and least privilege access controls.

</p>
<br />

<p>
<img width="1624" height="981" alt="AD-VM User Automate Before" src="https://github.com/user-attachments/assets/782a59d0-1aef-4753-a285-3b6f5861523c" />
</p>
<p>
  
- Opened PowerShell ISE as the domain administrator to prepare an automation script for bulk user account creation within Active Directory.

</p>
<br />

<p>
<img width="1624" height="979" alt="AD-VM User Automate After" src="https://github.com/user-attachments/assets/568839bb-a522-436d-b51d-b223028c4c0b" />
</p>
<p>
  
- Executed the PowerShell script to automatically create multiple standard domain user accounts within the _EMPLOYEES organizational unit, verifying successful account creation in ADUC.

</p>
<br />

<p>
<img width="1624" height="981" alt="Client-1 VM NonAdmin Login" src="https://github.com/user-attachments/assets/14c674d0-469c-4800-8987-830d6d8c1240" />
</p>
<p>
  
- Logged into Client-1 using a newly created standard domain user account to verify successful domain authentication and non-administrative user access.

</p>
<br />

---

## Skills Developed

### Active Directory Domain Services (AD DS) Administration

Gained hands-on experience installing and configuring Active Directory Domain Services, promoting a Windows Server system to a domain controller, and managing a domain-based environment.

### Windows Server Administration

Configured and managed a Windows Server environment using Server Manager, including server role installation, system configuration, and domain controller management.

### Microsoft Azure Infrastructure Management

Worked within Microsoft Azure to manage cloud-hosted virtual machines used to simulate an on-premises Active Directory environment.

### Remote Desktop Administration

Used Remote Desktop Protocol (RDP) to remotely access, configure, and manage both server and client virtual machines.

### Domain User and Administrative Account Management

Created and managed domain user accounts, administrative accounts, and security group memberships within Active Directory.

### Organizational Unit (OU) Management

Configured Organizational Units (OUs) to organize administrative and standard user accounts for improved directory structure and account management.

### Domain Join Configuration

Configured a client virtual machine to join the Active Directory domain, enabling centralized authentication and domain-based access control.

### Domain Authentication Verification

Tested and verified successful domain authentication using both administrative and non-administrative user accounts.

### PowerShell Automation

Used PowerShell ISE to execute automation scripts for bulk domain user account creation, demonstrating basic scripting and automation within an Active Directory environment.

### Identity and Access Management (IAM) Fundamentals

Developed practical experience with account provisioning, privilege assignment, authentication, and access control within a Windows domain environment.

### Remote Access Configuration

Configured Remote Desktop access for domain users within a controlled lab environment to validate user authentication and access permissions.

### Technical Documentation

Documented infrastructure deployment, Active Directory configuration, account management, and authentication testing through structured technical documentation and screenshots.
