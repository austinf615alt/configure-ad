<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Windows Server Manager
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used </h2>

- Windows Server 2025 Datacenter X64 Gen2 

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Create and Configure Azure Infrastructure
- Step 2: Deploy Windows Server Virtual Machines
- Step 3: Install and Configure Active Directory Domain Services
- Step 4: Join Client Systems and Configure Policies

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="2560" height="1280" alt="LAB4-DCDEPLOY" src="https://github.com/user-attachments/assets/76bb93ad-ea5e-48da-9013-530e3aa7c930" />
</p>
<p>
Create the Azure environment needed for the domain deployment by setting up a Resource Group, then create two Virtual Machines using Windows Server 2025 images, one named Client-1, and one named Domain-Controller, making sure the Virtual Network and subnets match so the Virtual Machines can communicate internally. Configure the Domain-Controller to have a static IP under network settings so clients can locate it reliably for domain services, then change the DNS settings of Client-1 to point to the Domain Controller's static IP address so they can properly resolve and communicate with the domain. 
</p>
<br />

<p>
PLACEHOLDER
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
PLACEHOLDER
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
