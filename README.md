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

- Windows Server 2025 Datacenter X64 Gen2 

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1: Created and Configure Azure Infrastructure
- Step 2: Deployed Windows Server Virtual Machines
- Step 3: Installed and Configured Active Directory Domain Services
- Step 4: Created and Configured Administrative and Organizational Structure
- Step 5: Joined a Client System to Domain.

<h2>Deployment and Configuration Steps</h2>

Step 1: Created and Configured Azure Infrastructure:

<p>
<img width="2560" height="1280" alt="LAB4-DCDEPLOY" src="https://github.com/user-attachments/assets/76bb93ad-ea5e-48da-9013-530e3aa7c930" />
</p>
<p>
  
- Created the Azure environment needed for the domain deployment by setting up a Resource Group, then created two Virtual Machines using Windows Server 2025 images, one named Client-1, and one named Domain-Controller, noting down and setting up an administrator account for both and making sure the Virtual Network and subnets match so the Virtual Machines can communicate internally. 

- Configured the Domain-Controller to have a static private IP under network settings so client system can locate it reliably for domain services, then changed the DNS settings of Client-1 to point to Domain-Controller's static IP address so they can properly resolve and communicate with the domain. 
</p>
<br />

Step 2: Deployed Windows Server Virtual Machines:

IMAGE NOTE: Client-1 is left image, Domain-Controller is right image.

<p>
<img width="2560" height="1070" alt="image" src="https://github.com/user-attachments/assets/e981d2ae-0c35-4a81-8bfe-e612dc8bffc2" />
</p>
<p>
  
- Once deployed, remoted into both the Client-1 Virtual Machine and the Domain-Controller Virtual Machine using Remote Desktop Connection. Used the public IP address given to each respective Virtual Machine to sign in and use the administrator accounts made during the Azure setup to remote into each system. 
  
- Once signed in to each system, opened Powershell in each system to observe and verify that the network configurations were correct. On the Client-1 system, typed in "ipconfig /all" to observe that the DNS points to the Domain Controller's static IP address, then typed in "ping x.x.x.x" (replace x.x.x.x with the static private ip address of your domain controller) and observe that it pings the Domain-Controller's private IP address. 
</p>
<br />

Step 3: Installed and Configured Active Directory Domain Services:

<p>
<img width="2103" height="1257" alt="LAB4-ADSERVICE" src="https://github.com/user-attachments/assets/06fa70ff-3b9e-482d-b90c-f2ee2beb52f7" />
</p>
<p>
  
- Installed and configured Active Directory Domain Services within Server Manager on Domain-Controller Virtual Machine, promoting the server to a Domain Controller with the domain name "mydomain.com" to provide centralized authentication, DNS, and domain management services. Verified domain was set up and new tools such as "Active Directory Users and Computers" and "Group Policy Management" were available.

</p>
<br />

Step 4: Created and Configured Administrative and Organizational Structure

<p> 
<img width="2182" height="1230" alt="image" src="https://github.com/user-attachments/assets/93c7c993-934a-45ba-bcfb-de37453e1b16" />
</p>
<p>

- Made an Organizational Unit named _ADMINS inside Active Directory Users and Computers, adding two new users name John Doe and Jane Doe to the _ADMINS group, then giving them membership in the Domain Admins group to grant them administrative privileges across the domain. Verified that both users had administrative privileges by signing into their accounts on the Domain-Controller Virtual Machine.

</p> 
<br />

Step 5: Joined Client Systems and Configure Policies

<p>
<img width="1792" height="1072" alt="LAB4-CLIENT2DC" src="https://github.com/user-attachments/assets/7690ac42-3051-4dfa-a42e-ad4ad76add18" />
</p> 
<p> 

- Joined the Client-1 Virtual Machine to the domain by ensuring the DNS was properly pointing to Domain-Controller's static private IP Address, going into system settings and giving Client-1 membership on the "mydomain.com" domain. Verified by signing into Client-1 with Domain Admin account. 
