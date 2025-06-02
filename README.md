<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>
<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines, completed as part of the CourseCareers IT course. The project demonstrates setting up a domain controller, configuring Active Directory Domain Services (AD DS), and managing users and groups to simulate an enterprise environment, with testing using mock users.

<h2>Environments and Technologies Used</h2>
Microsoft Azure (Virtual Machines/Compute)

Remote Desktop

Active Directory Domain Services (AD DS)

PowerShell

DNS (Domain Name System)

<h2>Operating Systems Used</h2>
Windows Server 2022

Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>
Provision Azure Virtual Machines: Set up a Windows Server 2022 VM as the domain controller and a Windows 11 VM as a client.

Install and Configure AD DS: Promote the Windows Server to a domain controller and configure Active Directory.

Join Client to Domain: Configure the Windows 11 VM to join the Active Directory domain.

Manage Users and Groups: Create and manage mock users and groups in AD to simulate organizational roles.

Test Functionality: Validate domain authentication and user access using mock accounts.

<h2>Deployment and Configuration Steps</h2>

<p>
<b>Step 1: Provision Azure Virtual Machines</b><br />
- Log in to the Microsoft Azure portal and create two virtual machines:
  - DC-VM (Domain Controller): Windows Server 2022 with at least 2 vCPUs and 4GB RAM.
  - Client-VM: Windows 11 (21H2) with at least 1 vCPU and 2GB RAM.
- Configure a virtual network (VNet) to ensure both VMs can communicate.
- Assign static private IP addresses to the VMs for consistent DNS configuration.
- Enable Remote Desktop Protocol (RDP) on both VMs and note their public IP addresses for access.
- Connect to both VMs using Remote Desktop to verify connectivity.
</p>
<br />

<p>
<b>Step 2: Install and Configure Active Directory Domain Services</b><br />
- On the DC-VM, open Server Manager and add the Active Directory Domain Services role.
- Install the role and promote the server to a domain controller using the Active Directory Domain Services Configuration Wizard.
- Create a new forest and configure DNS settings during promotion.
- Set a Directory Services Restore Mode (DSRM) password.
- After promotion, verify that the DNS server is running and that the domain is active using PowerShell.
</p>
<br />

<p>
<b>Step 3: Join Windows 11 Client to the Domain</b><br />
- On the Client-VM, configure the network adapter to use the DC-VM’s private IP address as the DNS server.
- Open System Properties, navigate to Computer Name, and select Change to join the domain.
- Provide credentials for an AD administrator account to authenticate the join.
- Restart the Client-VM and log in with a domain account to verify successful domain joining.
</p>
<br />

<p>
<b>Step 4: Create and Manage Users and Groups</b><br />
- On the DC-VM, open Active Directory Users and Computers.
- Create an Organizational Unit to organize users.
- Create mock user accounts and assign them to appropriate groups.
- Configure group policies to restrict or grant permissions to specific users or groups.
- Test user authentication by logging into the Client-VM with mock user credentials.
</p>
<br />
<h2>Testing and Validation</h2>

<p>
<b>Step 5: Testing Active Directory Functionality</b><br />
- Created multiple mock user accounts in Active Directory to simulate an organizational environment.
- Tested domain login from the Client-VM using mock user credentials to verify authentication.
- Validated group membership by restricting access to specific resources for certain users.
- Used PowerShell to query AD objects to confirm proper configuration.
- Tested connectivity and DNS resolution between the domain controller and client to ensure a stable environment.
</p>
<br />
