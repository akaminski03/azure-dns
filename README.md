<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

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
From client, attempt to ping and nslookup an ip that does not exist.
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
From client, Successfully ping and nslookup "apple."
</p>
<br />
