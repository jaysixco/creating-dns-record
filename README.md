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
<strong>Simplified Version:</strong><br>
<strong>Log into DC-1 </strong><br>
<strong>Create a DNS A-record for "mainframe"</strong><br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Server Manager > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Tools (near top, to the right of the flag > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - DNS > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - <em>Insert screenshot here </em><br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Click "DC-1" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Click "Forward Looking Zone" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Click "mydomain.com" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Right click the white space > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Click New Host (A) > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Type mainframe > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Type whatever IP address (public or private?) you want (prof used dc-1's as an example) ><br> 
&nbsp;&nbsp;&nbsp;&nbsp;   - Click Add Host (don't have to click any of the checkboxes above) > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - Click Done <br>
<strong> Log into Client-1 </strong><br>
<strong> Type "cmd" in search bar > then ping "mainframe" (without quotation marks) </strong><br>


<strong> Local DNS Cache Exercise </strong><br>
<em> What is going on here? <br>
Basically, if you change the mainframe's record address, when you ping it, it will still show the old record address until you flush the DNS cache. <br>
<strong>To see for yourself: </strong>
</em> <br>
&nbsp;&nbsp; - Log in to DC-1 and change mainframe’s record address to 8.8.8.8 <br>
&nbsp;&nbsp; - Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address <br>
&nbsp;&nbsp; - Observe the local dns cache (ipconfig /displaydns) <br>
<strong>How to flush the DNS cache </strong><br>
&nbsp;&nbsp; - Flush the DNS cache **(ipconfig /flushdns)**. <br>
&nbsp;&nbsp; - Ping “mainframe” again. The new record address should show up <br>

<strong> CNAME Record Exercise </strong><br>
<em> What is going on here? <br>

</em>
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com” <br>
<strong>To create a CNAME record</strong><br>
&nbsp;&nbsp; - DNS manager ><br>
&nbsp;&nbsp; - Right click + select New Alias (literally says CNAME) ><br>
&nbsp;&nbsp;&nbsp;&nbsp;   - <em>Insert screenshot here </em><br>
&nbsp;&nbsp; - Literally type search in first box and www.google.com in second box (literally sooooooo easy 😩) ><br>
&nbsp;&nbsp; - Do I need to check box? Nope > <br>
&nbsp;&nbsp; - Click ok <br>
&nbsp;&nbsp;&nbsp;&nbsp;   - <em>Insert screenshot here </em><br>
<strong> Switch to Client-1 </strong><br>
&nbsp;&nbsp; - Ping “search” <br>
&nbsp;&nbsp; - Nslookup “search” <br>
<strong>If you did everything correctly you should see</strong><br>
&nbsp;&nbsp;&nbsp;&nbsp;   - <em>Insert screenshot here </em>
<br>
<strong>NOTE:</strong> if above steps don't work, try flushing the cache first (ipconfig /flushdns) and then ping again. <br>
<br>
<strong> Finish </strong>
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
