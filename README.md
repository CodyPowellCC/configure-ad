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

Join Client to Domain: Configure the Windows 10 VM to join the Active Directory domain.

Manage Users and Groups: Create and manage mock users and groups in AD to simulate organizational roles.

Test Functionality: Validate domain authentication and user access using mock accounts.

<h2>Deployment and Configuration Steps</h2>
<p>
<img src="https://i.imgur.com/YOUR_SCREENSHOT_1.png" height="80%" width="80%" alt="Creating Azure VMs"/>
</p>
<p>
<b>Step 1: Provision Azure Virtual Machines</b><br />
- Log in to the Microsoft Azure portal and create two virtual machines:
  - **DC-VM (Domain Controller)**: Windows Server 2022 with at least 2 vCPUs and 4GB RAM.
  - **Client-VM**: Windows 10 (21H2) with at least 1 vCPU and 2GB RAM.
- Configure a virtual network (VNet) to ensure both VMs can communicate (e.g., use the same VNet and subnet).
- Assign static private IP addresses to the VMs for consistent DNS configuration.
- Enable Remote Desktop Protocol (RDP) on both VMs and note their public IP addresses for access.
- Connect to both VMs using Remote Desktop to verify connectivity.
</p>
<br />
<p>
<img src="https://i.imgur.com/YOUR_SCREENSHOT_2.png" height="80%" width="80%" alt="Installing AD DS"/>
</p>
<p>
<b>Step 2: Install and Configure Active Directory Domain Services</b><br />
- On the DC-VM, open Server Manager and add the **Active Directory Domain Services** role.
- Install the role and promote the server to a domain controller using the Active Directory Domain Services Configuration Wizard.
- Create a new forest (e.g., `mydomain.com`) and configure DNS settings during promotion.
- Set a Directory Services Restore Mode (DSRM) password.
- After promotion, verify that the DNS server is running and that the domain is active using PowerShell (`Get-ADDomain`).
</p>
<br />
<p>
<img src="https://i.imgur.com/YOUR_SCREENSHOT_3.png" height="80%" width="80%" alt="Joining Client to Domain"/>
</p>
<p>
<b>Step 3: Join Windows 10 Client to the Domain</b><br />
- On the Client-VM, configure the network adapter to use the DC-VM’s private IP address as the DNS server.
- Open System Properties, navigate to Computer Name, and select **Change** to join the domain (e.g., `mydomain.local`).
- Provide credentials for an AD administrator account to authenticate the join.
- Restart the Client-VM and log in with a domain account to verify successful domain joining.
</p>
<br />
<p>
<img src="https://i.imgur.com/YOUR_SCREENSHOT_4.png" height="80%" width="80%" alt="Managing AD Users"/>
</p>
<p>
<b>Step 4: Create and Manage Users and Groups</b><br />
- On the DC-VM, open **Active Directory Users and Computers** (ADUC).
- Create an Organizational Unit (OU) to organize users (e.g., `IT_Department`).
- Create mock user accounts (e.g., `user1`, `user2`, `admin1`) and assign them to appropriate groups (e.g., `IT_Staff`, `Admins`).
- Configure group policies (optional) to restrict or grant permissions to specific users or groups.
- Test user authentication by logging into the Client-VM with mock user credentials.
</p>
<br />
<h2>Testing and Validation</h2>
<p>
<img src="https://i.imgur.com/YOUR_SCREENSHOT_5.png" height="80%" width="80%" alt="Testing AD with Mock Users"/>
</p>
<p>
<b>Step 5: Testing Active Directory Functionality</b><br />
- Created multiple mock user accounts in Active Directory to simulate an organizational environment.
- Tested domain login from the Client-VM using mock user credentials to verify authentication.
- Validated group membership by restricting access to specific resources (e.g., shared folders) for certain users.
- Used PowerShell to query AD objects (`Get-ADUser`, `Get-ADGroup`) to confirm proper configuration.
- Tested connectivity and DNS resolution between the domain controller and client to ensure a stable environment.
</p>
<br />
