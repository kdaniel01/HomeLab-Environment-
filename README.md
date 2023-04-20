<img src="https://i.imgur.com/IJn3nj0.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />


<h2>Description</h2>

<b>In this project,I created a lab environment using Windows Server 2022 to set up and configure a fully functioning Active Directory Domain Services as well as a DNS and DHCP server.
</b>


<h2>Environments and Technologies Used</h2>

- <b> Oracle Virtual Box<br /> 
- <b> Virtual Machine (Windows Server 2022)<br /> 
- <b> Virtual Machine (Windows 10 Pro)<br />
- <b>Active Directory Domain Services<br />
- <b>DNS Services<br />
- <b>DHCP Services<br />

<h2>Overview </h2>
- <b>Part 1- Creating Domain Controller from Windows Server 2022<br />
- <b>Part 2- Joining client machine to tunetech.local domain<br />
- <b>Part 3- Installing and configuring DHCP Role on Domain Controller<br />
 
 
<h2>Part 1- Creating Domain Controller from Windows Server 2022:</h2>

<p align="center">
I created a VM to be used as Domain Controller for an organization called "Tunetech". The VM will be configured with Server Manager. "DC-1-Win2022" was created and the Network setting was configured for Adapter 1 to be attached to the Internal Network.<br />
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
<h2>Part 2- Joining client machine to tunetech.local domain:</h2>
The IP address of the Windows 10 client vm was 10.0.2.15 and default gateway 10.0.2.2 which we would need to change. The deafult gateway should be set to the IP of the Domain Controller DC-1 (10.0.0.1).<br/>
<p align="center">
<img src="https://i.imgur.com/CpwooHe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/eyAX9Ao.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
 <br />
 <br />
 <p align="center">
We can see that the Windows 10 client machine has connectivity to DC-1.<br/>
<img src="https://i.imgur.com/dQy5wCL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
 <br />
 <p align="center">
 Navigated to System > Advanced system settings > Computer Name > Change. Added tunetech.local domain which was successful.<br />
<img src="https://i.imgur.com/tKHwZXB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <br />
<img src="https://i.imgur.com/iej6Z4R.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <br />
 <img src="https://i.imgur.com/ysNxqwg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
We can see that the A record was added automatically for the Windows 10 client machine confirming that the DNS server is functioning correctly.<br/>
<img src="https://i.imgur.com/Dzx7NUH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
 <br />
 <br />
 <br />
<h2>Part 3- Installing and configuring DHCP Role on Domain Controller:</h2>

<p align="center">
In Server Manager, the following steps were performed- Add roles and features > Check DHCP Server box > Check Restart the destination server automatically if required.This installed the DHCP server role needed.<br/>
<img src="https://i.imgur.com/NLCS4Qa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
<img src="https://i.imgur.com/CavhOMx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br />
<img src="https://i.imgur.com/OmUEnXH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
 <br />
 <br /> 
<p align="center">
The DHCP post-install configuration was then performed. Used tunetech admin credentials to authorize the DHCP server in AD DS. <br/>
<img src="https://i.imgur.com/u69Rwlp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/XuLlyeR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/0RsICMG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />

<p align="center">
Set the duration for the scope leases to 180 days. The Default Gateway was set to 10.0.0.60. <br/>
<img src="https://i.imgur.com/8GWQRMt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/aWY8Kl9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/T2bxdpW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/9FtWTIB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />

 <p align="center">
The DHCP server was then restarted for the configurations to be applied. The windows 10 client machine IPv4 settings were changed to automatically obtain an IP and DNS server address. Verified that the DHCP server assigned an IP from the pool to this client machine which it did(10.0.0.10).<br/>
<img src="https://i.imgur.com/ZJHLtOl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/aoOYjJF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/mvSZkQp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/4bAsIEV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<img src="https://i.imgur.com/H7axNwi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<br />
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
