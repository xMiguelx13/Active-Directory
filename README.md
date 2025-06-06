# Active-Directory<h1> Oracle VirtualBox/Adding Users with PowerShell</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
This project consists of using Oracle VirtualBox with Windows Server 2019 and Windows 10 to create a network and add users using PowerShell in an automated way to the system. 


Here, we will create a Domain Controller (DC) inside of a Virtual Machine, that will house the network machines' two network adapters. One of the network adapters will connect to the internet, while the other one will connect to the private network created. On this DC we will install Windows Server 2019.
On the DC, we will create our domain as "mydomain.com" and install Active  Directory. We will then configure NAT and Routing so that the inside Active Directory can get access to the internet.
We will also set up a DHCP on the DC, so that clients can get on the network.

We will then use PowerShell to add users into the Active Directory.

Finally, we will start another virtual machine and install Windows 10. This will have the private users that will go into the network we have created above.


<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>LINUX/Ubuntu</b>
- <b>Oracle VirtualBox</b> 

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Windows Server 2019</b>

<h2>Program walk-through:</h2>

<p align="center">
Installing Windows Server 2019 and Windows 10 on computer: <br/>
<img src="https://i.imgur.com/6L1uSQk.png" height="80%" width="80%" alt="Installing Windows Server 2019"/>
<br />
<br />
Adding Windows Server 2019 to VirtualBox:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
