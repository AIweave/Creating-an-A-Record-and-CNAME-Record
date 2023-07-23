
![cname](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/c89f6dfe-f7e4-4865-9bae-01f78aeec060)


<h1>Creating an A - Record and CNAME Record in DNS</h1>

This tutorial will distinguish an A-Record from a CNAMe and instruct how to create each.<br />

**Must Know** - [A-Records](https://support.google.com/a/answer/2576578?hl=en#:~:text=An%20A%20record%20maps%20a,configured%20for%20one%20domain%20name.&zippy=%2Chow-a-records-work%2Cconfigure-a-records-now) are mappings that link domain names to physical computer IP addresses.  A [CNAME Record](https://en.wikipedia.org/wiki/CNAME_record) is a type of DNS record that maps an alias or subdomain name to it's true domain. 

<h2>Video Demonstration</h2>

- ### [YouTube: How to create, work, and resolves tickets within osTicket](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Microsoft Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b>
- Windows Server 2022 (as Domain Controller)

<h2>Instructions</h2>

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

Finish
