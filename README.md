# creating-dns-record

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />
In this tutorial, you are going to play 3 roles:  administrator, agent, user <br>
In this tutorial, you/we are going to be creating and delegating tickets <br>

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
A-Record Exercise
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as an admin (mydomain\jane_admin)
From Client-1 try to ping “mainframe” notice that it fails
Nslookup “mainframe” notice that it fails (no DNS record)
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works

Local DNS Cache Exercise
Go back to DC-1 and change mainframe’s record address to 8.8.8.8
Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address
Observe the local dns cache (ipconfig /displaydns)
Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty
Attempt to ping “mainframe” again. Observe the address of the new record is showing up

CNAME Record Exercise
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record
On Client-1, nslookup “search”, observe the results of the CNAME record
Extra steps  (basically checking to see if everything works)

Finish

Essential Steps:
Create a DNS A-record (5)
Change mainframe record address to 8.8.8.8 (7)
Flush the DNS cache (10)
Create CNAME record (12)
Recognize the pattern of above steps?

Actually…

You can combine steps 5, 7, and 12 all in one. So really it COULD look like:

Create a DNS A-record (name it mainframe, put the IP address as 8.8.8.8, click ok) and then create a CNAME record (search, www.google.com)
Go to cmd (run as admin, still in DC-1), type (in order):
ipconfig /flushdns, 
ping search
nslookup search
ipconfig /displaydns 

</p>
<br />
<p>

</p>
<p>

</p>


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
