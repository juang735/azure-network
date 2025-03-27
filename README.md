<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/GU1S98z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I was able to created a resources group, watch virtual network and subnets, create 2 VM my windowws and linux [Ubuntun] and create a network security groups [firewall resource] 
</p>
<br />

<p>
<img src="https://i.imgur.com/UopgWkL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We start to check all the traffic from one machine to another we ping icpm from one machine and look for a ping an make sure the ip is thesame. In the linux VM we close ICMPv4 port 290 we denied any traffic coming to and from. Observe SSH Traffic, start a packet capture up Filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address, Observe DHCP Traffic. filter for DHCP traffic only
Open PowerShell as admin and run: ipconfig /renew
Observe the DHCP traffic appearing in WireShark, Observe DNS Traffic
 filter for DNS traffic only
 within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark. Observe RDP Traffic
 filter for RDP traffic only (tcp.port == 3389)
</p>
<br />

<p>
<img src="https://i.imgur.com/oGqzOF2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Wireshark allows as to filter traffic to focus on specific packets. For example:
To see HTTP traffic, type http in the filter bar and hit Enter.
To capture traffic from a specific IP address, type ip.addr == 192.168.1.1 (replace with the actual IP) in the filter bar. As you capture traffic, each packet will be displayed in a list with details such as source/destination IP, protocol, and length.

we can click on any packet to view its detailed information, including headers and payload, also follow specific packet streams (like TCP streams) by right-clicking a packet and selecting "Follow" > "TCP Stream."


