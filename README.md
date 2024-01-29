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
<p>
  Navigate to Azure Portal:

Go to Azure Portal and sign in to your Azure account.
Create Virtual Machines:

In the Azure Portal, navigate to "Virtual machines" and create two or more VMs with Windows Server installed.
</p>
<p>
Virtual Network:
Create a Virtual Network in Azure to connect the Azure VMs. Define subnets and configure network security groups.
</p>

<p>
  Connect to VMs:
Use Microsoft Remote Desktop to connect to each Azure VM. Retrieve the public IP addresses for each VM from the Azure Portal.</p>

<p>
  Install AD DS Role:

On one VM, open PowerShell as an administrator and run the following command to install the AD DS role:
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
</p>

<p>
  After installation, promote the VM to a domain controller using the following command:
  Install-ADDSForest -DomainName yourdomain.local -DomainMode 4 -ForestMode 4 -InstallDns
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Verify Domain Controller Status:
Use PowerShell commands like Get-ADDomainController to verify the status of the domain controllers.
</p>


<p>
  Configure DNS Settings:
Ensure that DNS settings on each VM point to the IP address of the domain controller.
</p>

<p>
  Create OUs:
Use Active Directory Users and Computers (ADUC) to create organizational units (OUs) for organizing objects within Active Directory.</p>

<p>
  Configure Group Policies:
Use the Group Policy Management Console (GPMC) to create and apply Group Policies for managing settings across the domain.</p>


<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Add Users and Computers:
Use ADUC to add user accounts and computer accounts to the Active Directory domain.</p>

<p>
  PowerShell for AD Tasks:
Utilize PowerShell for various Active Directory tasks, such as user creation, group management, and organizational unit manipulation.</p>

<p>
  Backup AD Data:

Implement regular backups of Active Directory using Windows Server Backup or other backup solutions.
Disaster Recovery Plan:

Establish a disaster recovery plan, including regular testing of backups and recovery procedures.</p>
<br />
