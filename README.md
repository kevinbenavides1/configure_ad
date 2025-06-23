<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<p>
  
![The_Office-logo](https://github.com/user-attachments/assets/f27f9f4c-a809-41f6-b94a-67bb32656b4b)
</p>
Will be setting up an Active Directory for The Office, a new paper company that has moved into Columbus, Ohio!

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Powershell


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Network Topology Overview</h2>
Initial Active Directory Setup (Used for this project)<br />
<img width="608" alt="Screenshot 2025-06-22 at 1 31 52 PM" src="https://github.com/user-attachments/assets/ff3164a2-eb6e-496a-9371-5bcd453e2232" /><br />
Foundational Active Directory deployment within an Azure virtual network. It includes:<br />

- DC-1 (Domain Controller):
  - A Windows Server VM configured with a static private IP (10.0.0.x) and set as the DNS server for the domain.<br />
  - Hosts Active Directory Domain Services (AD DS) and DNS.<br />

- User-1 (Client VM):
  - Joined to the mydomain.com domain.
  - Configured to use DC-1's IP as its DNS server to ensure domain resolution.<br />
  
This setup provides a working domain environment where client machines can resolve domain services, authenticate users, and access domain resources.<br />
<br />
<br />
Expanded Domain Integration (Enterprise Environments)<br />
<img width="710" alt="Screenshot 2025-06-22 at 1 32 00 PM" src="https://github.com/user-attachments/assets/f14ab902-614c-4b72-bebe-777fdf7ee29d" /><br />
Represents the scaling of the domain to include multiple client machines:<br />

- Eight user computers (User-1 to User-8) are joined to the domain controlled by DC-1.<br />
- Each client system communicates with the domain controller for authentication, policy enforcement, and resource access.<br />
- This reflects a centralized identity and access management model typical in enterprise environments. <br />





<h2>High-Level Deployment and Configuration Steps</h2>

  <h3>Set Up Domain Controller(DC)  </h3>
  - Deployed a new Windows Server VM to serve as the Domain Controller.<br />
  - Configured the Network Interface Card (NIC) with a static private IP address.<br />
  - Assigned the same static IP as the primary DNS server, since this server will also run DNS.
  <h3>Set Up User VM</h3>
  - Created a Windows client VM in the same region and Virtual Network as the Domain Controller.<br />
  - Configured the User VM's DNS settings to point to the DC's private IP.<br />
  - Verified DNS settings using ipconfig /all and tested name resolution via ping.
  <h3>Install and Configure Active Directory Domain Services (AD DS)</h3>
  - On the DC, installed Active Directory Domain Services and associated management tools.<br />
  - Promoted the server to a Domain Controller.<br />
  - Created a new forest and domain: mydomain.com
  <h3>Create Administrative User</h3>
  - In Active Directory Users and Computers (ADUC), created a new user named Kevin Benavides.<br />
  - Added Kevin to the Domain Admins security group for administrative rights. *Note: In a productive environement, delegate only necessary permissions to avoid excessive privilege.*
  <h3>Join User Computer to the Domain</h3>
  - Logged into the User VM as a local administrator.<br />
  - Joined the computer to the mydomain.com domain.<br />
  - Verified the join by logging in with the domain admin credentials.<br />
  - Confirmed that the computer appears in ADUC > Computers.
  <h3>Configure Remote Desktop Access</h3>
  - As Kevin Benavides (Domain Admin), enabled Remote Desktop access on the User VM.<br />
  - Allowed domain users to connect via Remote Desktop.<br />
  <h3>Organize AD Structure</h3>
  - Created a new Organizational Unit (OU) named COMPS and moved the User computer into this OU.<br />
  - Created additional OUs to reflect the organizational structure of The Office (Ohio Branch).
  <h3>Create Domain Users</h3>
  - Created user accounts for employees of The Office.
  - Placed users into their appropriate OUs based on department/location.
  - Ensured naming conventions were consistent.
  
  
  
 

<h2>Deployment and Configuration Steps</h2>
<h3>Domain Controller Setup</h3>
<p>
<img width="2391" alt="Screenshot 2025-06-22 at 7 56 26 PM" src="https://github.com/user-attachments/assets/36a45b93-2573-4806-b5cd-36caaf3a4cb7" />
</p>
<p>
Domain Controller (DC-1) with Active Directory Domain Services and DNS roles successfully installed. On the right, ipconfig /all confirms the server's static IP configuration (10.0.0.4) and DNS settings, which are essential for proper domain name resolution and communication between domain-joined devices.
</p>
<br />

<p>
<img width="359" alt="Screenshot 2025-06-22 at 8 07 28 PM" src="https://github.com/user-attachments/assets/826759a7-3634-4772-aefb-964cb949ccc9" />
</p>
<p>
mydomain.com was successfully created and the server was promoted to a Domain Controller. Active Directory tools recognize the domain, confirming that the promotion process was completed. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
