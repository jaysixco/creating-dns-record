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
&nbsp;&nbsp;&nbsp;&nbsp;   1. On the Server Manager page, look for Tools (top right hand corner, to the right of the flag), and then click DNS <br>
  <br>
<img width="959" alt="Capture - Tools + DNS" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/c60fa30d-a54a-45f6-8830-1f6f7f2e1f3b">
<br>
&nbsp;&nbsp;&nbsp;&nbsp;   2. Click "DC-1" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   3. Click "Forward Looking Zone" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   4. Click "mydomain.com" in the sidebar > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   5. Right click the white space > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   6. Click New Host (A) > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   7. Type mainframe > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   8. Type whatever IP address you want (ex: cmd > ipconfig > private IP address) ><br> 
&nbsp;&nbsp;&nbsp;&nbsp;   9. Click Add Host (don't have to click any of the checkboxes above) > <br>
&nbsp;&nbsp;&nbsp;&nbsp;   10. Click Done <br>
  <br>
<strong> Ping the mainframe to see if it works </strong><br>
  1. Log into Client-1 <br>
  2. Type "cmd" in search bar <br>
  insert screenshot <br>
  3. Then ping "mainframe" (without quotation marks), If it works, you should the word "Reply" repeatedly. Like this:<br>
  <img width="354" alt="Capture - ping + nslookup" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/3e623d41-fa39-45d4-8f65-87ec24e9a23e">

<strong> Local DNS Cache Exercise </strong><br>
<em> What is going on here? <br>
Basically, if you change the mainframe's record address, when you ping it, it will still show the old record address until you flush the DNS cache. <br>
<strong>To see for yourself </strong>: 
</em> <br>
<strong> Log in to DC-1 and change mainframe’s record address to 8.8.8.8 </strong><br> 
  1. Log in to DC-1 <br>
  2. Forward looking zone <br>
  3. mydomain.com <br>
  4. Right click mainframe <br>
  5. Properties <br>
  6. Type 8.8.8.8 in IP address box <br>
  7. Click "Apply" <br>
  8. Click "Ok" <br>
  <em> insert screenshots sonewhere in above steps </em>
<br>
&nbsp;&nbsp; 1. Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address (you'll recieve replies from the old IP address) <br>
&nbsp;&nbsp; 2. Observe the local dns cache (ipconfig /displaydns). It will show that A (Host) Record is still the old address. <br>
<strong> Flush the DNS cache </strong><br>
&nbsp;&nbsp; 1. Switch back to DC-1. <br>
&nbsp;&nbsp; 2. Flush the DNS cache (run cmd as an administrator) **(ipconfig /flushdns)**. <br>
&nbsp;&nbsp; 3. Ping “mainframe” again . The new record address should show up <br>
<br>

<br>
<strong> CNAME Record Exercise </strong><br>
<em> What is going on here? <br></em>
Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com” <br>
<strong> Create a CNAME record</strong><br>
&nbsp;&nbsp; 1. DNS manager <br>
&nbsp;&nbsp; 2. Right click + select New Alias (literally says CNAME) ><br>
<img width="565" alt="Capture - New Alias (CName)" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/46d6ecb9-e0b7-47cb-904f-9c2801ac33d1">
<br>
&nbsp;&nbsp; 3. Type "search" in the first box and "www.google.com" in second box <br>
<img width="300" alt="Capture - search + google" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/77628443-22e4-4616-a93e-ec581dc1230c">
insert screenshot <br>
&nbsp;&nbsp; 4. Do I need to check box? Nope <br>
&nbsp;&nbsp; 5. Click "Ok" <br>

<br>
<strong> 6. Switch to Client-1 </strong><br>
&nbsp;&nbsp; 7. Ping “search” <br>
&nbsp;&nbsp; 8. Nslookup “search” <br>
<strong>If you did everything correctly you should see</strong><br>
<br>
<strong>NOTE:</strong> if above steps don't work, try flushing the cache first (ipconfig /flushdns) and then ping again. <br>
<br>
<strong> Finish </strong>

<p>
  Accurate and can follow along. Fix formatting.
</p>
