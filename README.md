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

Step 1: Create and Configure Azure Infrastructure:

<p>
<img width="2560" height="1280" alt="LAB4-DCDEPLOY" src="https://github.com/user-attachments/assets/76bb93ad-ea5e-48da-9013-530e3aa7c930" />
</p>
<p>
  
- Create the Azure environment needed for the domain deployment by setting up a Resource Group, then create two Virtual Machines using Windows Server 2025 images, one named Client-1, and one named Domain-Controller, noting down and setting up an administrator account for both and making sure the Virtual Network and subnets match so the Virtual Machines can communicate internally. 

- Configure the Domain-Controller to have a static private IP under network settings so clients can locate it reliably for domain services, then change the DNS settings of Client-1 to point to the Domain Controller's static IP address so they can properly resolve and communicate with the domain. 
</p>
<br />

Step 2: Deploy Windows Server Virtual Machines:

IMAGE NOTE: Client-1 is left image, Domain-Controller is right image.

<p>
<img width="2560" height="1070" alt="image" src="https://github.com/user-attachments/assets/e981d2ae-0c35-4a81-8bfe-e612dc8bffc2" />
</p>
<p>
  
- Once deployed, remote into both the Client-1 Virtual Machine and the Domain-Controller Virtual Machine using Remote Desktop Connection. Use the public IP address given to each respective Virtual Machine to sign in and use the administrator accounts made during the Azure setup to remote into each system. 
  
- Once signed in to each system, open Powershell in each system to observe and verify that the network configurations are correct. On the Client-1 system, type in "ipconfig /all" to observe that the DNS points to the Domain Controller's static IP address, then type in "ping x.x.x.x" (replace x.x.x.x with the static private ip address of your domain controller) and observe that it pings the Domain-Controller's private IP address. 
</p>
<br />

Step 3: Install and Configure Active Directory Domain Services:

<p>
<img width="2103" height="1257" alt="LAB4-ADSERVICE" src="https://github.com/user-attachments/assets/06fa70ff-3b9e-482d-b90c-f2ee2beb52f7" />
</p>
<p>
  
- On the Domain-Controller system, go into Server Manager which should boot up automatically, and click on Manage > Add Roles and Features at the top right corner. At the installation wizard, select next at the "Before You Begin" tab, in the Installation Type tab; select "Role-based or feature-based installation" then click next, in the Server Selection tab; select your specific server (Should just be your own in this exercise) then click next. At the Server Roles tab; select Active Directory Domain Services and install, allowing necessary features to install as well.

- Once installed, Server Manager should prompt to "Promote as a Domain Controller", select this and at the wizard, select "Add New Forest" and add your desired domain name in the "Root Domain Name" box. Once done, take care to make sure both the functional levels match Windows Server 2025. Note down and set a Directory Services Restore Mode password then select next and move forward to install the configuration. Allow the server to restart. Once complete, verify that the server is set up as a domain controller by going into "Local Server" in Server Manager, and observing that the domain is set, and checking that you have access to "Active Directory Users and Groups", "Active Directory Domains and Trusts", and "Group Policy Management" in the tools bar.

</p>
<br />

Step 4: Join Client Systems and Configure Policies:

</p> 

