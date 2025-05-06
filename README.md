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

- Create our Virtual Machines
- Observe ICMP Traffic
- Configuring a Firewall (Network Security Group)
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/9sxozHT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Creating a Resource Group:
  
- Create a Windows 10 Virtual Machine 
- Create a Linux (Ubuntu) 
- Ensure both VMs are in the same Virtual Network / Subnet

</p>
<br />

<p>
<img src="https://i.imgur.com/RPJPvDq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing ICMP Traffic:

- Use Remote Desktop to connect to Windows 10 Virtual Machine
- Within Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and start packet capture
- Within Wireshark, filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
- Observe ping requests and replies within WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/odHGIEF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configuring a Firewall (Network Security Group):
  
- Initiated a perpetual/non-stop ping from Windows 10 VM to Ubuntu VM
- Opened the Network Security Group on the Ubuntu VM and disable incoming (inbound) ICMP traffic
- Back in the Windows 10 VM, observed the ICMP traffic in WireShark and the command line Ping activity
- Re-enabled ICMP traffic for the Network Security Group to the Ubuntu VM
- Back in the Windows 10 VM, observed the ICMP traffic in WireShark and the command line Ping activity

</p>
<br />

<p>
<img src="https://i.imgur.com/1xoRwpB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing SSH Traffic:
  
- In Wireshark, Filter for SSH traffic only
- Open PowerShell, and type: ssh labuser@<private IP address>
- Typed commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe DHCP Traffic:
  
- In Wireshark, filter for DHCP traffic only
- In PowerShell as admin run: ipconfig /renew
- Observe the DHCP traffic appearing in WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe DNS Traffic:
  
- In Wireshark, filter for DNS traffic only
- From Windows 10 VM within a command line, used nslookup to see what google.com and disney.com’s IP addresses are
- Observe the DNS traffic being show in WireShark

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observing RDP Traffic:

- in Wireshark, filter for RDP traffic only (tcp.port == 3389)
- Observe the immediate non-stop spam of traffic

</p>
<br />
