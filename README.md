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
<strong> A-Record Exercise </strong><br>
  <em>Basically, log into Client-1 <br>
    ping "mainframe" <br>
    nslookup "mainframe" <br>
    (Both are going to fail because there is no DNS record) <br>
    So, log into DC-1 with your domain admin account (mydomain.com\jane_admin) and create a DNS A-record for "mainframe" <br>
    Have the DNS A-record point to DC-1’s Private IP address <br>
    Log back into Client-1 and ping "mainframe" again. It should work this time. <br></em>
<strong>Simplified Version:</strong>
&nbsp;&nbsp; Log into DC-1 <br>
&nbsp;&nbsp; Create a DNS A-record for "mainframe" <br>
&nbsp;&nbsp; Log into Client-1 <br>
&nbsp;&nbsp; Ping "mainframe" <br>


<strong> Local DNS Cache Exercise </strong><br>
<em> What is going on here? <br>
Basically, if you change the mainframe's record address, when you ping it, it will still show the old record address until you flush the DNS cache.
To see for yourself:
</em>
&nbsp;&nbsp; Log in to DC-1 and change mainframe’s record address to 8.8.8.8 <br>
&nbsp;&nbsp; Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address <br>
&nbsp;&nbsp; Observe the local dns cache (ipconfig /displaydns) <br>
<strong>How to flush the DNS cache </strong><br>
&nbsp;&nbsp; Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty <br>
&nbsp;&nbsp; Attempt to ping “mainframe” again. Observe the address of the new record is showing up <br>

<strong> CNAME Record Exercise </strong><br>
<em> What is going on here? <br>

</em>
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com” <br>
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record <br>
On Client-1, nslookup “search”, observe the results of the CNAME record <br>
Extra steps  (basically checking to see if everything works) <br>
&nbsp;&nbsp; Cmd > <br>
ping search > <br>
ipconfig /displaydns <br>
[Should see: <br>
search <br>
Record name: search mydomain.com <br>
Record name: www.google.com] <br>

ALSO: if above steps don't work, trying flushing the cache first (ipconfig /flushdns) and then repeat. <br>

If you type search mydomain.com into Microsoft Edge, it'll try to take you to Google (but it'll show error because certificates don't match, still we forced it to acknowledge search as google. Main thing is the cmd part).<br>

<strong> Finish </strong>

Essential Steps:
Create a DNS A-record (5) <br>
&nbsp;&nbsp; Server Manager > Tools (near top, to the right of the flag > DNS > Expand DC-1 > Expand Forward Looking Zone > click mydomain.com > right click white space > select New Host (A) > type mainframe > type whatever IP address you want (prof used dc-1's as an example) > click Add Host (don't have to click any of the checkboxes above) > click Done <br>
Change mainframe record address to 8.8.8.8 (7) <br>
Flush the DNS cache (10) <br>
Create CNAME record (12) <br>
&nbsp;&nbsp; DNS manager (to get here, follow same steps as step 5) > Right click + select New Alias (literally says CNAME) > Literally type search in first box and www.google.com in second box (literally sooooooo easy 😩) > Do I need to check box? Nope > Click ok <br>
Recognize the pattern of above steps? <br>

















<strong> A-Record Exercise </strong><br>
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin) <br>
Connect/log into Client-1 as an admin (mydomain\jane_admin) <br>
From Client-1 try to ping “mainframe” notice that it fails <br>
Nslookup “mainframe” notice that it fails (no DNS record) <br>
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address <br>
Go back to Client-1 and try to ping it. Observe that it works <br>

<strong> Local DNS Cache Exercise </strong><br>
Go back to DC-1 and change mainframe’s record address to 8.8.8.8 <br>
Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address <br>
Observe the local dns cache (ipconfig /displaydns) <br>
Flush the DNS cache (ipconfig /flushdns). Observe that the cache is empty <br>
Attempt to ping “mainframe” again. Observe the address of the new record is showing up <br>

<strong> CNAME Record Exercise </strong><br>
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com” <br>
Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record <br>
On Client-1, nslookup “search”, observe the results of the CNAME record <br>
Extra steps  (basically checking to see if everything works) <br>
&nbsp;&nbsp; Cmd > <br>
ping search > <br>
ipconfig /displaydns <br>
[Should see: <br>
search <br>
Record name: search mydomain.com <br>
Record name: www.google.com] <br>

ALSO: if above steps don't work, trying flushing the cache first (ipconfig /flushdns) and then repeat. <br>

If you type search mydomain.com into Microsoft Edge, it'll try to take you to Google (but it'll show error because certificates don't match, still we forced it to acknowledge search as google. Main thing is the cmd part).<br>

<strong> Finish </strong>

Essential Steps:
Create a DNS A-record (5) <br>
&nbsp;&nbsp; Server Manager > Tools (near top, to the right of the flag > DNS > Expand DC-1 > Expand Forward Looking Zone > click mydomain.com > right click white space > select New Host (A) > type mainframe > type whatever IP address you want (prof used dc-1's as an example) > click Add Host (don't have to click any of the checkboxes above) > click Done <br>
Change mainframe record address to 8.8.8.8 (7) <br>
Flush the DNS cache (10) <br>
Create CNAME record (12) <br>
&nbsp;&nbsp; DNS manager (to get here, follow same steps as step 5) > Right click + select New Alias (literally says CNAME) > Literally type search in first box and www.google.com in second box (literally sooooooo easy 😩) > Do I need to check box? Nope > Click ok <br>
Recognize the pattern of above steps? <br>

Actually… <br>

You can combine steps 5, 7, and 12 all in one. So really it COULD look like: <br>

Create a DNS A-record (name it mainframe, put the IP address as 8.8.8.8, click ok) and then create a CNAME record (search, www.google.com) <br>
Go to cmd (run as admin, still in DC-1), type (in order): <br>
ipconfig /flushdns, <br>
ping search <br>
nslookup search <br>
ipconfig /displaydns <br>

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
