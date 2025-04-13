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
To create a ressource group, click <a href="https://github.com/Annorbi/Ressource-Group"> here 
<p>
To create a virtual machine, click <a href="https://github.com/Annorbi/Virtual-Machines"> here 
</p>
</p>
<br />

<p>
<img src="https://i.imgur.com/1t2CgDm.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/1G8byry.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/PDRqQxl.png" height="30%" width="30%"
</p>
<p>
Make sure both your windows PC and server pc are turned on and active. On the azure portal, go to home→Virtual machines→[Server VM name]→Network→Network Interface Card→ip config and set the allocation to static.
</p>
<br />

<p>
<img src="https://i.imgur.com/szk2PsH.png" height="60%" width="60%"
</p>
<p>
Next, go through the same thing for the Client PC but instead of changing the allocation, you'll change the ip address to that of the windows server pc's private IP in the dns settings.
</p>
<br />

<p>
<img src="https://i.imgur.com/QR281kT.png" height="60%" width="60%" 
</p>
<p>
From the windows PC, ping the server PC's private address to make sure things work. You should be able to do this as both PC should be "connected". You be able to see a screen like this one, where the two PCs are communicating with each other.
</p>
<br />

<p>
<img src="https://i.imgur.com/14pmlnG.png" height="60%" width="60%" 
</p>
<p>
Next, you can very the connection by typing the command "ipconfig /all" and make sure that the [dns settings] match the private ip adress of the DC1 from earlier. From there, you are ready to deploy Active Directory.
</p>
<br />

<h2>Deploying Active Directory</h2>

<p>
<img src="https://i.imgur.com/fYl7wl9.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/EYzG8SR.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/SZowAcZ.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/UrzXIYr.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/EYzG8SR.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/mqHfJEt.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/uN8TLfu.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/WgOwxCe.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/2NY39jM.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/Df9gDOp.png" height="30%" width="30%"
</p>
<p>
On the windows server, install active directory <b>domain services</b>. Make sure to follow very closely.
</p>
<br />

<p>
<img src="https://i.imgur.com/oHJmP3s.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/0SLf2Sw.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/n0fzds6.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/qM3dNjs.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/udJiHnt.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/Gql08LO.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/0mTSLe4.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/aQvkhJ3.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/rvn9C4Y.png" height="30%" width="30%" 
</p>
</p>
<p>
Once you have the domain services installed, it is time to configure it by promoting as a DC (Domain Controller); setup a new forest (name your domain and take note of it). In the next screen, create a password and also take note of it. Don't forget to disable the dns settings, we won't need those. Afterwards, you can just press "next" to most of the pages. Once you reach the end, you'll be prompted to "install". Go ahead and do so; once the install finishes, you'll probably lose connection; do not panic, this is normal and your VM will be restarted.
</p>
<br />


<p>
<img src="https://i.imgur.com/sKetQDA.png" height="60%" width="60%" 
</p>
<p>
Once you log back in, make sure to log in as a domain user by typing "[domain name here]\username" and input your password as usual. So in this case here it would look like this: mydomain.com\labuser
</p>
<br />

<p>
<img src="https://i.imgur.com/kUUt5Zi.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/joebe15.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/pFM23XA.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/WbUFdRd.png" height="30%" width="30%" <p> <img src="https://i.imgur.com/KMAj5jT.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/TYjm8Hd.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/QSMoBTX.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/3ucqEXg.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/GgYdzCJ.png" height="30%" width="30%"  <p> <img src="https://i.imgur.com/nJMoaaU.png" height="30%" width="30%" 
</p>
<p>
Next, we need to test out the domain by creating both OUs (Organiasational Units) as well as users. To create an Ou, simply find "tools", "Active Directory Users and Computers" → [domain name] (right click it) → new → Organizational Unit. For this example, we will be creating the Admin, Employees, and Clients OUs. We are using the the "_" to help us easily find our newly created groups. To do so, [domain name] (right click) → new → user. Give this user <i>"domain admin"</i> rights. This is not to be confused for regular <i>"admin"</i>; the two are not the same. Lastly, go to the "builtin" and "remote dekstop users", add the user you just created in "member of". Once you are done with all of that, try to log in using your newly created admin. We will be using this account from now on. Make sure to set the password to "never expire" and take note of it, you'll need it later.
</p>
<br />


<h2>Joining the Client pc to the domain</h2>


<p>
</p>
<p>
Make sure your VM was restarted and then get ready to join your client pc (windows PC) to the newly created domain.
</p>
<p>
<img src="https://i.imgur.com/8djCy2i.png" height="40%" width="40%" <p> <img src="https://i.imgur.com/ZQ2uveK.png" height="40%" width="40%"
</p>
<p>
Make sure to right-click and hit "propreties" 
</p>
<br />


<p>
<img src="https://i.imgur.com/HqIT6ey.png" height="60%" width="60%" 
</p>
<p>
Find "advance system settings" and then locate the <i>network id</i>.
</p>
<br />


<p>
<img src="https://i.imgur.com/nTo8HMg.png" height="60%" width="60%" 
</p>
<p>
Add in the admin account and password you created over in the previous step. For this example, it'll be "Jane Doe". For the domain name, you'll need to enter the domain name you created earlier. In this example, we used "mydomain.com". Once done, hit "next".
</p>
<br />

<p>
<img src="https://i.imgur.com/D3ttMF5.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/2jdBOyw.png" height="40%" width="40%"
</p>
<p>
Make sure the info's good and then press "next" a couple of times. Your vm will be restarted to join the domain, that's all good. Wait for it to be done and once it is, log back in. You can verify that you are in fact registered to the domain by once again right clicking on "my pc" and finding "system propreties".
</p>
<br />

<p>
<img src="https://i.imgur.com/J654ATf.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QSTQj5W.png" height="40%" width="40%" <p> <img src="https://i.imgur.com/SFF6jGH.png" height="40%" width="40%"
</p>
<p>
Next, make sure to allow "domain users" to login to this PC; this will be required for the next step.
</p>

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Once everything is all setup, go back to the server and find the "Computers" tab in active directory. You should now be able to see the windows PC. Go ahead and drag and drop it over to the "_CLIENTS" OU we created a while ago. Once you are done with that, we can move on to the next stage.
</p>
<br />

<h2>Spoofing employees</h2>

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Now, we will create a script that will generate a bunch of fake employees for testing purposes. Switch back to DC1 (windows server pc) and open powershell ISE as an administrator.
</p>
<br />

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Paste the provided script <a href="https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1"> <br /> to generate as many users as desired (maybe stick to 100 or less).
</p>
<br />

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Once everything is all setup, go back to the server and find the "Computers" tab in active directory. You should now be able to see the windows PC. Go ahead and drag and drop it over to the "_CLIENTS" OU we created a while ago. Once you are done with that, we can move on to the next stage.
</p>
<br />

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Observe the newly created users under the “_EMPLOYEES” OU. Choose a random employee name and login as them from the client PC. Before you do this though, make sure to allow them to remote connect. The username will be their "name". The default password will be "Password1". For example, we will try to login as "cumu.fin". So, we would enter "mydomain.com\cumu.fin" as the username and "Password1" for the password.
</p>
<br />

<p>
<img src="https://i.imgur.com/0OxAnHb.png" height="40%" width="40%"  <p> <img src="https://i.imgur.com/QjIYKrx.png" height="40%" width="40%"
</p>
<p>
Once everything is all setup, go back to the server and find the "Computers" tab in active directory. You should now be able to see the windows PC. Go ahead and drag and drop it over to the "_CLIENTS" OU we created a while ago. Once you are done with that, we can move on to the next stage.
</p>
<br />

<h2>Practicing handling user account settings</h2>


Dealing with Account Lockouts
Get logged into dc-1
Pick a random user account you created previously
Attempt to log in with it 10 times with a bad password

Configure Group Policy to Lockout the account after 5 attempts:
How To Configure Account Lockout Threshold in Group Policy

Attempt to log in with it 6 times with a bad password

Observe that the account has been locked out within Active Directory
Unlock the account
Reset the password
Attempt to login with it

Enabling and Disabling Accounts
Disable the same account in Active Directory
Attempt to login with it, observe the error message
Re-enable the account and attempt to login with it.

Observing Logs
Observe the logs in the Domain Controller
Observe the logs on the client Machine
Precursor to cybersecurity and security operations: joshmadakor.tech/cyber

GPMC.MSC → Group Policy Managment → Forest → Domains → Default domain Policy
