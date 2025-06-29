# Active-Directory<h1> Oracle VirtualBox/Adding Users with PowerShell</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
This project consists of using Oracle VirtualBox with Windows Server 2019 and Windows 10 to create a network and add users using PowerShell in an automated way to the system. 


Here, we will create a Domain Controller (DC) inside of a Virtual Machine, that will house the network machines' two network adapters. One of the network adapters will connect to the internet, while the other one will connect to the private network created. This will allow for the Windows 10 Client to connect to the internet via the DC network. On this DC we will install Windows Server 2019.
On the DC, we will create our domain as "mydomain.com" and install Active Directory. We will then configure NAT and Routing so that the inside Active Directory can get access to the internet.
We will also set up a DHCP on the DC, so that clients can get on the network.

We will then use PowerShell to add users into the Active Directory.

Finally, we will start another virtual machine and install Windows 10. This will have the private users that will go into the network we have created above. Here, we will make sure other users are able to log in and connect to the internet. This VM we will name Client1, and we will also reset a password for the user (mrayas).

This would conclude the project.


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
<img src="https://i.imgur.com/6L1uSQk.png" height="80%" width="80%" alt="Installing Windows 10"/>
<img src="https://i.imgur.com/LsAdKbM.png" height="80%" width="80%" alt="Installing Windows Server 2019"/>
<br />
<br />
Adding Windows Server 2019 to VirtualBox:
 Here, I am naming the server DC for Domain Controller as well as giving the server 2GB of memory and to run on 3 CPUs <br/>
<img src="https://i.imgur.com/PxOJlXV.png" height="80%" width="80%" alt="Adding WS2019 to VB"/>
<br />
<br />
In settings on the Windows Server 2019, I added on Adapter 1; NAT which will give me access to the outside internet, and then I added Adapter 2; Internal. This Adapter 2 will serve as the conduit between the outside internet and our clients. 
 The internal network will give the clients access to the server: <br/>
<img src="https://i.imgur.com/udpqPbj.png" height="80%" width="80%" alt="WS2019 Settings"/>
<br />
<br />
For the next step, I installed Windows Server 2019 on a VM using VirtualBox:  <br/>
<img src="https://i.imgur.com/mmgnN0o.png" height="80%" width="80%" alt="Installing Windows Server 2019"/>
<br />
<br />
I then set up the NIC (Internal) internet within the network. Marking my IP as 172.16.0.1. My mask 255.255.255.0, and my DNS as pinging itself as 127.0.0.1:  <br/>
<img src="https://i.imgur.com/siTBHIn.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
After setting up the IP address,  I created the Active Directory Domain Controller. Giving it the name "mydomain.com":  <br/>
<img src="https://i.imgur.com/HXmS6g7.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/YGPw2F2.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Now it is time to set up an admin account instead of using the one windows provides
In order to do this, we had to create a new group within the system called "_ADMINS". We then added user mrayas (my name) and moved the user to the admins folder:  <br/>
<img src="https://i.imgur.com/8jsLNrC.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/Y6F9rGj.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Now we will install RAT (Remote Access Server)/NAS (Network Access Translation) in order to allow our client from Windows 10 to be on the network and have access to the internet:  <br/>
<img src="https://i.imgur.com/2mBfzAC.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/QakoxT5.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Following the installation of RAT/NAS, we will set up our DHCP which will allow a client (user) to join our network and sign on. Here, we w ill set the scope from: 172.16.0.100 to 172.16.0.200.: </br>
<img src="https://i.imgur.com/G47ArB6.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/XPdMu7E.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Ones we have successfully set up our Active Directory Domain Controller, we will use PowerShell in order to add 1,000 random names into our Server. This will serve as the "users" or clients within our organization. In this list, I will also include my name (Miguel Rayas) to create a regular user within the organization. </br>
<img src="https://i.imgur.com/Ajxogpq.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/doUPpr6.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/guvUCFj.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
In the final step, we will create a Windows 10 VM that will serve as a client of the network we created above.

<br />
<br />
(Troubleshooting) We did have an issue because the client was not wanting to connect to our DNS server for some reason.(First picture) So what I found was that private IP addresses in a lab do not like to connect to themselves. To solve this issue, I double checked my steps to make sure I had the DNS server role in place. Next, under DHCP manager, I made sure the option "003 Router" was in place with the internal IP of (192.168.0.1). Secondly, I made sure that option "006 DNS Servers" also had our DC's IP Address. This pretty much told our client to use the DC a sour DNS server Lastly, I made sure to restart the DNS server and renew our ipconfig inside of the Command Prompt in the Client VM. For proof that we successfully connected to the internet, we were able to ping 'www.google.com'. </br>
<img src="https://i.imgur.com/igDtS91.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/e6ROTCu.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/GKA9IRn.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/dTpdpT8.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/IvZLqjN.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
In the final steps, we will rename the computer to "CLIENT1" and attempt to join the domain "mydomain.com". After successfully joining the domain, we will go back to the DHCP manager in the DC VM and make sure that the computer is apart of the network we have created. As you can see, everything looks great! </br>
<img src="https://i.imgur.com/CzlG2eq.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/Y4BUNrl.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/z9gRY7V.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Finally, to make sure the new users are able to log in, we will attempt to log into our CLIENT1 computer with a different user that is in our system. (Do remember that our admin accounts start with an "a-" within the username.</br>
<img src="https://i.imgur.com/CzlG2eq.png" height="80%" width="80%" alt="VM"/>
<img src="https://i.imgur.com/Y4BUNrl.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
Lastly, to double check that the client is under our DC ecosysteme, we will go back out to our DHCP manager inside our DC and go into our leases. Here, we should see that there should be a lease taken up by our client (which is currently running).
<img src="https://i.imgur.com/deZxFJX.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
For the final piece, we changed the password for the user (mrayas). Doing this, we have also practiced what would seem like the most common problem within IT. In order to do this, we went to manage users and computers in our DC. Under _USERS, we found the user (mrayas), and reset the password.
<img src="https://i.imgur.com/S12R2RP.png" height="80%" width="80%" alt="VM"/>
<br />
<br />
</p>

<br />
<br />
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
