<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Observing the Domain Name System between Azure Virtual Machines</h1>
In this tutorial, we observe how the domain name system behaves using Azure Virtual Machines. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>List of Prerequisites</h2>

- Active Directory running in Azure on a virtual machine 
- A client machine running in Azure on a virtual machine and joined to the domain

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/81408b9a-524e-4c62-b128-900bc86479d8" height="80%" width="80%" alt="apple1"/>
</p>
<p>
From client, attempt to ping and nslookup a domain that does not exist, and does not have an ip.
</p>
<br />

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/ae1b27eb-c9c1-471b-b1e5-4859537cdc12" height="80%" width="80%" alt="a-record"/>
</p>
<p>
From domain controller, create a new A Record / Host named "apple."
</p>
<br />

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/ff6c30fd-daa1-4c2c-8150-4f48a3fdf550" height="80%" width="80%" alt="apple2"/>
</p>
<p>
From client, successfully ping and nslookup "apple." This simply resolves the domain "apple" to the local ip address of the domain controller. It is retrieving this information from the DNS server.
</p>
<br />

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/6b98f930-6ccc-423a-bde7-82fc1fe831aa" height="80%" width="80%" alt="apple3"/>
</p>
<p>
The local cache now has a record, which is much faster than pinging the DNS server.
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/5670c2c9-8d41-4a9c-8198-ea4db6edfa28" height="80%" width="80%" alt="apple4"/>
</p>
<p>
From domain controller, change the A record of "apple" to use the ip address "8.8.8.8" 
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/d637fb2b-7551-448c-9949-807a90fb7963" height="80%" width="80%" alt="apple5"/>
</p>
<p>
From client, ping "apple" and notice that despite changing the A record. Since the ip address is in the local cache, it checks the local cache first and resolves it, depsite being incorrect.
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/33b3ad7f-de89-4e36-857c-894afcc7a601" height="80%" width="80%" alt="apple6"/>
</p>
<p>
From client, flush the DNS, now there is no record of "apple."
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/a74fe964-ecbe-4569-bf79-43e0caeaa696" height="80%" width="80%" alt="apple6"/>
</p>
<p>
From client, ping "apple" once again. Since it is not found in the cache, it is forced to retrieve it from the DNS server, which now displays the updated ip address.
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/1e33e32f-af9e-4073-a596-6d6b3f3ab6b3" height="80%" width="80%" alt="apple7"/>
</p>
<p>
From domain, create a new CNAME called search. It will simply resolve back to "apple", "apple.domain.com".
</p>

<p>
<img src="https://github.com/akaminski03/azure-network-protocols/assets/65532146/039b432c-3bcc-4b31-8bdd-1cf4d57519a2" height="80%" width="80%" alt="search"/>
</p>
<p>
From client, ping "search". It is now mapped to apple.domain.com, which has an ip of 8.8.8.8
</p>

