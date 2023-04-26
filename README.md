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

<h2>High-Level Steps</h2>

- Create Virtual Machines (Ubuntu & Windows 10)
- Remote Desktop into VM
- Observe ICMP Traffic
- Observe ping requests and replies within WireShark
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/snW3jUC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

- Create a Windows 10 Virtual Machine (VM)

- Create a Linux (Ubuntu) VM
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From The Windows 10 VM, I opened command line/PowerShell & attempted to ping a public website (such as www.google.com) and observed the traffic in WireShark.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiated a perpetual/non-stop ping from Windows 10 VM to Ubuntu VM
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I Opened the Network Security Group which is what my Ubuntu VM is using and disabled incoming (inbound) ICMP traffic
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in the Windows 10 VM, I observed the ICMP traffic in WireShark and the command line Ping activity
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Re-enabled ICMP traffic for the Network Security Group my Ubuntu VM is using
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observed the ICMP traffic in WireShark and the command line Ping activity (which it started working)
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
SSH into my Ubuntu Virtual Machine (via its private IP address)
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
Type “Exit” to stop ssh activity
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Windows 10 VM, I attempt to issue my VM a new IP address from the command line (ipconfig /renew) & Observed the DHCP traffic appearing in WireShark
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From your Windows 10 VM within a command line, I used nslookup to see what google.com and disney.com’s IP addresses are
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, I filtered for RDP traffic only (tcp.port == 3389) & observed the immediate non-stop spam of traffic. 

- the RDP (protocol) is constantly showing a live stream from one computer to another, therefor traffic is always being transmitted
</p>
<br />
