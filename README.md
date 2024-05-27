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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> <br>
</p>
<p>
<strong> A-Record Exercise </strong><br>
  <em>Basically, log into Client-1 <br>
    ping "mainframe" <br>
    nslookup "mainframe" <br>
    (Both are going to fail because there is no DNS record) <br>
    So, log into DC-1 with your domain admin account (mydomain.com\jane_admin) and create a DNS A-record for "mainframe" <br>
    Have the DNS A-record point to DC-1’s Private IP address <br>
    Log back into Client-1 and ping "mainframe" again. It should work this time. </em>
  
<strong>Simplified Version:</strong><br>
<strong>Log into DC-1 </strong><br>
<strong>Create a DNS A-record for "mainframe"</strong><br>
1. On the Server Manager page, look for Tools (top right hand corner, to the right of the flag), and then click DNS <br>
  <br>
<img width="959" alt="Capture - Tools + DNS" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/c60fa30d-a54a-45f6-8830-1f6f7f2e1f3b">
  <br>
&nbsp; 2. Click "DC-1" in the sidebar (1), Click "Forward Looking Zone" in the sidebar (2), Double click "mydomain.com" in the sidebar (3) <br>
(Dc1,#1)
&nbsp; 3. Right click the white space, Click "New Host (A or AAAA)" <br>
(Dc1,#2)
&nbsp; 4. For the "Name" type mainframe <br>
&nbsp; 5. For the IP address, open up command prompt, type "ipconfig" (1) and look at the number for "IPv4 Address" (2)
(dc1,#3)
&nbsp; 6. After you type the "Name" and "IP address" click Add Host. After it is added, click "Done"
(dc1,#4)

<strong> Ping the mainframe to see if it works </strong><br>
1. Log in to Client-1 <br>
2. Type "cmd" in search bar (see screenshot) <br>
3. Then ping "mainframe". If it works, you should the word "Reply" repeatedly, like this: //insert screenshot below, red rectangle box around word(s) "Reply"

<strong> Local DNS Cache Exercise </strong><br>
<em> What is going on here? <br>
Basically, if you change the mainframe's record address, when you ping it, it will still show the old record address until you flush the DNS cache. <br>
<strong>To see for yourself </strong>: 
</em>

<strong> Log in to DC-1 and change mainframe’s record address to 8.8.8.8 </strong><br> 
1. Log in to DC-1 <br>
2. Click "Forward Looking Zone" <br>
3. Click "mydomain.com" <br>
4. Right click "mainframe" <br>
5. Click "Properties" <br>
6. Type 8.8.8.8 in IP address box <br>
7. Click "Apply" <br>
8. Click "Ok" <br>
  <em> insert screenshots sonewhere in above steps </em>
  
<strong> Go back to Client-1 and ping “mainframe” again </strong>. 
1. Observe that it still pings the old address (you'll recieve replies from the old IP address) (see screenshot)<br>

<strong> Observe the local dns cache </strong>.
1. In the command prompt, type "ipconfig /displaydns". It will show that A (Host) Record is still the old address. </strong> (see screenshot)<br>

<strong> Flush the DNS cache </strong>
1. Run cmd as an administrator. Type "cmd" in the start menu search box, right click "Command Prompt", and click "Run as an administrator" (see screenshot) <br>
2. Type "ipconfig /flushdns" then type "ping mainframe” again.  The new record address should show up </strong> (see screenshot)<br>

<strong> CNAME Record Exercise </strong><br>
<em> What is going on here? <br></em>

<strong> Go back to DC-1 and create a CNAME record that points the host "search" to "google.com"</strong><br>
1. Open the DNS manager. In the Server page, look for Tools (top right hand corner, to the right of the flag), and then click DNS (see screenshot, copy and paste it from line 52)
2. Right click any white section of the screen, then click "New Alias (CNAME)" ><br>
<img width="565" alt="Capture - New Alias (CName)" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/46d6ecb9-e0b7-47cb-904f-9c2801ac33d1">
<br>
3. Type "search" in the first box and "www.google.com" in the second box <br>
<img width="300" alt="Capture - search + google" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/77628443-22e4-4616-a93e-ec581dc1230c"><br>
4. Leave the box unchecked and Click "Ok" (see screenshot) <br>
<br>
<strong> Switch to Client-1 </strong><br>
1. Open up the command prompt. Type "ping search” then hit enter. Type "nslookup search” then hit enter. <br>
2. If you did everything correctly you should see: </strong><br>
<img width="354" alt="Capture - ping + nslookup" src="https://github.com/jaysixco/creating-dns-record/assets/160427311/3e623d41-fa39-45d4-8f65-87ec24e9a23e"><br>
<br>
<strong>NOTE:</strong> if above steps don't work, try flushing the cache (type "ipconfig /flushdns") and then try step 1 again. <br>
<br>
<strong> Finish </strong>

<p>
  Accurate and can follow along. Fix formatting.
</p>
