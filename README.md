<img src="https://i.imgur.com/IJn3nj0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />


<h2>Description</h2>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<b>In this project,I deployed and configured an On premises Active Directory in Microsoft Azure using Virtual Machines.
</b>


<h2>Environments and Technologies Used</h2>

- <b> Oracle Virtual Box<br /> 
- <b> Virtual Machine (Windows Server 2022)<br /> 
- <b> Virtual Machine (Windows 10 Pro)<br />
- <b>Active Directory Domain Services<br />
- <b>DNS Services<br />
- <b>DHCP Services<br />
- <b>Remote Desktop<br />

<h2>Overview </h2>
- <b>Creating a Windows Server 2022 Virtual Machine with Oracle Virtual Box to be used as a Domain Controller.<br /> 
- <b>Checking for connectivity between Client Virtual Machines and Domain Controller<br />
- <b>Installing Active Directory and Admin Creation<br />



<h2>Part 1- Deploying Resources in Azure:</h2>

<p align="center">
I created a VMs to be used as Domain Controller for an organization called "Tunetech". The VM will be configured with Server Manager. "DC-1-Win2022" was created and Network settings was configured for Adapter 1 to be attached to the Internal Network.<br />
<img src="https://i.imgur.com/VpLeQSL.png" height="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/zAkGnVh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/zxmPiGu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then created the Active Directory Role in Server Manager.The vm was promoted to a Domain Controller role.<br/>
<img src="https://i.imgur.com/NAMsmlT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/2q8gIWn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/NDkulEu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/hM4Cexa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Created a new forest with root domain "tunetech.local". Be sure to put in the NetBIOS Domain name which would be "TUNETECH" for me. The DNS role was also be installed within this phase.<br/>
<img src="https://i.imgur.com/NAMsmlT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Er9Pzm7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/aWhthX3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<img src="https://i.imgur.com/RZHcB8P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/HxooUEp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
VM was restarted and as we can see the DNS role has been installed succu.DNS was installed successfully as we were able to ping our domain.<br/>
<img src="https://i.imgur.com/h5Ok0qS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/W67pnIL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/ZDGYuXG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/1N8J7Xz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Also verified that DC-1-Win2022 vm is now a Domain Controller by running "WMIC COMPUTERSYSTEM GET DOMAINROLE" command. Confirmed the domain role was 5 represents a DC.<br />
<img src="https://i.imgur.com/TBVMJUA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/kYPXiZ5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center">
Renamed DC-1-Win2022 server name from WIN-JQ4CP6H0M04 to DC-1.<br />
<img src="https://i.imgur.com/5YWyW0a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/GNgbVtP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

 
 

<br />
<p align="center">
<h2>Part 2- Joining client virtual machine to DC-1 domain controller:</h2>
Logged into Clientvm1 using RDP and attempted to ping the DCvm1's private IP which was unsuccessful as shown below.It failed because no Inbound ICMPv4 rule was created to allow this.<br/>
<p align="center">
<img src="https://i.imgur.com/TEszJLO.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
ICMPv4 Inbound rule was created on DCvm1 <br/>
<img src="https://i.imgur.com/EWkJYcR.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
<img src="https://i.imgur.com/xgR1w58.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Retried pinging the Domain Controller which was successful confirming connectivity.<br/>
<img src="https://i.imgur.com/XaAkgTX.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<h2>Part 3- Installing Active Directory and Admin Creation:</h2>

<p align="center">
Logged into to DCvm1 and installed Active Directorey Domain Services. Server manager > "Add roles and features" > Check the box for "Active Directory Domain Services" <br/>
<img src="https://i.imgur.com/G1CgBKh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
<img src="https://i.imgur.com/ruLMhY0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />

<p align="center">
Then promoted DCvm1 from server to Domain Controller.A new forrest was then configured.<br/>
<img src="https://i.imgur.com/UXuTINl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/Bnqe9Ct.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />


 <p align="center">
Restarted DCvm1 and logged in as user: dannytech.com\azureuser.Then launched Active Directory Users and Computers.<br/>
<img src="https://i.imgur.com/MTw8h31.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />


<p align="center">
Created a Organizational Units titled "EMPLOYEES"and "ADMINS". Then created an admin user for the "ADMINS" OU.<br/>
<img src="https://i.imgur.com/LNqBSqa.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 <img src="https://i.imgur.com/nVBc650.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 
 <p align="center">
This admin user was added to the "Domain Admins" Security Group.<br/>
<img src="https://i.imgur.com/LerYnEM.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
