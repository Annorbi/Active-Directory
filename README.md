<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setting up Active Directory
- Deploying Active Directory
- Joining a Client-PC to the domain
- Experimenting with user account settings

<h2>Setting up Active Directory</h2>

<p>
</p>
<p>
To begin, make sure you have a ressource group, as well as windows pc and a server pc up and running; you'll need both in this exploration. Links will follow if you do not know how to do either of these things.
<p>
To create a ressource group, click here.
<p>
To create a virtual machine, click here.
</p>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure both your windows PC and server pc are turned on and active. On the azure portal, goto home→Virtual machines→[Server VM name]→Network→Network Interface Card→ip config and set the allocation to static.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, go through the same thing for the Client PC but instead of changing the allocation, you'll change the ip address to that of the server pc's private IP. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From the windows PC, ping the server PC's private address to make sure things work. You should be able to do this as both PC should be "connected".
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
ipconfig /all and make sure that the [dns settings] are the private ip adress of the DC1
</p>
<br />

<h2>Deploying Active Directory</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On the windows server, install active directory;
  
</p>
<br />
