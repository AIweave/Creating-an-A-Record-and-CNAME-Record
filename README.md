
![cname](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/c89f6dfe-f7e4-4865-9bae-01f78aeec060) Figure 1.0


<h1>Creating an A - Record and CNAME Record in DNS</h1>

This tutorial will distinguish an A-Record from a CNAMe and instruct how to create each.<br />

**Must Know** - [A-Records](https://support.google.com/a/answer/2576578?hl=en#:~:text=An%20A%20record%20maps%20a,configured%20for%20one%20domain%20name.&zippy=%2Chow-a-records-work%2Cconfigure-a-records-now) are mappings that link domain names to physical computer IP addresses.  A [CNAME Record](https://en.wikipedia.org/wiki/CNAME_record) is a type of DNS record that maps an alias or subdomain name to it's true domain. (As shown in Figure 1.0).  

In order to follow these instructions, it is recommended to have a Virtual Machine (VM) connected to a Domain Contoller (DC) with Active Directory already setup. 

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

**Create an A-Record**
- Connect/log into DC-1 as your domain admin account. 
- Connect/log into Client-1 as an admin; same as the domain admin account (ex. mydomain.com\joe_admin).
- Go to Server Manager and click on "DNS" in the "Tools" tab.

![Screen Shot 2023-07-23 at 1 30 31 AM](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/c44e61ea-612f-40cd-bb78-17950f0355ff)

  
- Next, click on the name of Domain Controller.
- Click on Forward Lookup Zones, then your DC's forest name (created during Active Directory Installation).

![Screen Shot 2023-07-23 at 1 43 19 AM](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/8a07d945-3202-4242-a08a-55dc530f2e9b)

- On the right column, right click the mouse to select "New Host (A or AAAA)..."

![Screen Shot 2023-07-23 at 1 47 45 AM](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/200d990c-3516-4061-a04b-c0ee3cb19564)

- In the new pop-up window, create a domain name under "Name" with an IP address in the IP Address entry box and click "Add Host". For an example, Name: mainframe & IP Address: 8.8.8.8. 

![Screen Shot 2023-07-23 at 1 51 22 AM](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/ab2a85d0-0d30-4c9e-866e-30d4eece8bba)


- Go back to Client-1 (VM in use) and try to ping the A-Record previously created. Observe that it works.

![Screen Shot 2023-07-23 at 2 00 05 AM](https://github.com/AIweave/Creating-an-A-Record-and-CNAME-Record/assets/121763338/f3a5f2f1-fd01-41e4-8877-a4bdc40a0bfc)


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
