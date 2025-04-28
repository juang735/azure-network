<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>


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

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/GU1S98z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I successfully created a resource group to organize all my cloud resources. I then set up a virtual network and subnets to enable secure and isolated communication between resources. I deployed two virtual machines: one running Windows and the other running Ubuntu Linux, ensuring compatibility with both operating systems. Additionally, I created network security groups (NSGs) to act as firewall resources, controlling inbound and outbound traffic to the VMs. These NSGs were configured to enhance security by defining specific access rules. I also made sure to monitor the virtual network for traffic patterns and potential security threats. Overall, the setup provided a robust and secure cloud infrastructure.
</p>
<br />

<p>
<img src="https://i.imgur.com/UopgWkL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I began by checking the network traffic between two virtual machines. To do this, I can use ICMP from one machine to the other, ensuring that the IP addresses matched correctly. In the Linux VM, we closed the ICMPv4 port 290, effectively denying any incoming or outgoing traffic on that port. We then monitored SSH traffic by starting a packet capture and filtering for SSH traffic only. From the Windows 10 VM, we used SSH to connect to the Ubuntu virtual machine using its private IP address and observed the traffic. Next, we filtered for DHCP traffic and initiated a DHCP lease renewal by running the command ipconfig /renew in PowerShell (run as administrator). We observed the DHCP traffic in Wireshark as the lease renewal occurred. For DNS traffic, we filtered and used the nslookup command to resolve the IP addresses of websites like google.com and disney.com, while monitoring the DNS traffic in Wireshark. Finally, we filtered for RDP traffic (tcp.port == 3389) to observe the communication related to remote desktop sessions.
</p>
<br />

<p>
<img src="https://i.imgur.com/oGqzOF2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Wireshark let's me filter network traffic, so we can focus on specific packets. For instance, I see HTTP traffic, just typing 'http' in the filter bar and press Enter. If I want to capture traffic from a particular IP address, I can type ip.addr == 192.168.1.1 (just replace it with the actual IP address) in the filter bar. As the traffic is captured, each packet shows up in a list with details like the source and destination IP, the protocol, and its size. You can click on any packet to view detailed information, including headers and payload. Plus, you can follow specific packet streams, like TCP streams, by right-clicking on a packet and selecting 'Follow' > 'TCP Stream.' This makes it easy to track the flow of data and troubleshoot issues in real time.
</p>
<br />
<p>
<img src="https://i.imgur.com/O7TTmEn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To use various network protocols like SSH, RDP, DNS, HTTP/S, and ICMP, you simply need to interact with them through the appropriate tools or services. For example, SSH allows you to securely access a remote machine through a terminal, while RDP lets you remotely control another computer with a graphical interface. DNS is used to translate domain names into IP addresses, making it easier to browse websites. HTTP/S handles web traffic, ensuring secure communication between your browser and websites, and ICMP is used for diagnostics, like checking the connection status between devices through pinging. Each protocol serves a different purpose, but they all help facilitate communication across networks.
</p>
<br />
<p>
<img src="https://i.imgur.com/8uYSj2J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In a VPN (Virtual Private Network) is a technology that establishes a secure and private connection over the internet, allowing users to send and receive data as if their devices were directly linked to a private network. It's great for protecting your privacy, securing your internet traffic, and accessing content or resources as though you're on a different network. A VPN works by encrypting your internet traffic and routing it through a secure server, which hides your actual IP address. This helps prevent anyone from snooping on your online activities, whether you're using public Wi-Fi or just want an extra layer of security. Essentially, it creates a safe tunnel for your data to travel through, making it much harder for third parties to intercept or track your movements online.


