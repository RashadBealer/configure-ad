<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Azure Subscription
- Azure Virtual Network
- Azure Virtual Machines
- Azure Storage Account

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>Navigate to the Azure Portal and select your subscription.

Go to "Virtual networks" and create a new virtual network.

Define address spaces and subnets. Ensure connectivity between subnets.
</p>
<p>
Go to "Virtual machines" in the Azure Portal.

Create Windows Server VMs for Active Directory Domain Services (AD DS). Configure each VM with a unique static private IP.

On each VM, set the DNS server to the private IP address of the other VM (or itself if it's the first DC).
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the first VM:

Install AD DS by promoting the server to a domain controller.
Configure a new forest, specifying a domain name.
On subsequent VMs:

Install AD DS and join them to the existing domain.

Configure AD DS replication between domain controllers.

On one domain controller, enable the Global Catalog role.

Install the DHCP role on one of the domain controllers to provide IP addresses to machines on the network.

Configure DNS to support Active Directory. Ensure DNS zones are replicated across all domain controllers.

Define AD DS sites in Active Directory Sites and Services to optimize replication and logon traffic.

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join on-premises machines to the Azure AD DS domain. Update DNS settings on these machines to point to Azure AD DS DNS servers.

Verify AD DS functionality:
Ensure proper replication.
Test domain logons, user authentication, and group policy application.

Implement regular backups of Active Directory using Azure Backup or other backup solutions.

Establish a disaster recovery plan and test it to ensure quick recovery in case of issues.

Set up monitoring for Azure resources and Active Directory health.

Regularly update and patch Windows Server VMs.</p>
<br />
