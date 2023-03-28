<p align="center">
<img src="https://static.wixstatic.com/media/2ebf04_4302f0f9efbd490a84e66d0ea2a414bd~mv2.png" alt="Traffic Examination"/>
</p>
<br />

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we conduct an analysis of the different types of network traffic to and from Azure Virtual Machines using the Wireshark packet capture and analysis tool, as well as experiment with Network Security Groups.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://youtu.be/O3ISo0YCi5Q)

[![YouTube](https://static.wixstatic.com/media/2ebf04_d8e0a72a22634e3181fadf12cb47fbdb~mv2.png)](https://youtu.be/O3ISo0YCi5Q)
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command Prompt
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create two virtual machines: You'll need to create two virtual machines (VMs) that will serve as the traffic sources for network analysis. Use pre-built images, namely Windows 10 Pro Version 21H2 and Ubuntu Server 20.04 LTS. These VMs will communicate with each other within the same virtual network.
- Deploy Wireshark on the Windows 10 Pro VM: Once you have created the virtual machines, you will need to install the Wireshark network protocol analyzer software on the Windows 10 Pro VM. Wireshark captures and displays network traffic, allowing the user to inspect packets and analyze network behavior.
- Generate and analyze network traffic: Generate network traffic between the two VMs using various protocols such as Internet Control Message Protocol (ICMP), Secure Shell (SSH), Dynamic Host Configuration Protocol (DHCP), Domain Name System (DNS), and Remote Desktop Protocol (RDP). Capture and analyze the network traffic using Wireshark by applying filters for these protocols. This analysis will reveal important information such as source and destination IP addresses, and packet lengths, providing insights into the network's behavior and performance.

<h2>Actions and Observations</h2>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_74ce579cb3554e9e9a00af755dd07e7a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 1: Create a new resource group on Microsoft Azure.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_61e5bacfe40d4d22af40882a361f5fce~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 2: Set up an Azure virtual machine (VM) operating on Windows 10 Pro, Version 21H2.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_96bbdd6333ea4f8d8403f9420f954a46~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 3: Generate a username and password for the administrator account and proceed with creating the VM.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_04cca0787a69459190356b6feff09069~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 4: Create an additional virtual machine that operates on Ubuntu Server 20.04 LTS. Choose a username and password for the administrator account and include it in the same resource group and virtual network as the first VM.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cd1617d3c2e749da885e05752055a236~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 5: Connect to the first virtual machine using a remote desktop connection.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_b462864732e1497eaf73b416bec56483~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 6: Open Microsoft Edge and navigate to https://wireshark.org/download.html to download the latest version of Wireshark.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_10e47a6adb6f449588dea6f9a8438d50~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 7: Install Wireshark with the default installation settings.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_301150f264f8472793827b9f7ac8a87b~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 8: Begin capturing packets by launching Wireshark, clicking on the Ethernet option, and selecting the Blue Wireshark icon.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f1e2b1d34bdb4ac38a85c67a08642a99~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 9: Observe the traffic and filter it for ICMP traffic.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_986726791478472a873a8e0bc1b9c6e8~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 10: Using Windows PowerShell, ping the private IP address of the second virtual machine running Ubuntu Server and observe the traffic.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_373ac50481ce473ea35273fa68c9f533~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 11: Ping the second virtual machine non-stop using the -t command. Afterwards, proceed to block ICMP traffic from Azure for virtual machine 2.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_8967649fbb0d491a802599ce03260a23~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 12: Access the network security groups section, choose the second virtual machine, then navigate to Inbound security rules, and select "Add."
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_c953682793ce46f69b62ede583aa38b9~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 13: Keep the settings the same, but modify the protocol to ICMP, choose "Deny " for the action, set the priority to 299, and click on "Add."
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_13595cfa7ff042b6913e596de32dbe31~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 14: Notice how ICMP traffic has come to a halt due to the adjustments we made to block it.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_4b486f9531a8465ba31f4f6043daad20~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 15: Return to Inbound security rules in Azure, select "Allow" under action to enable ICMP traffic, and click on "Save".
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_20c36a1818e04221ba47a4771bbecf95~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 16: Observe the resumption of replies for ICMP traffic, and then press "Ctrl + C" to stop the non-stop ping.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_fa916015d0ed470aba66562c8de14edb~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 17: Filter for SSH traffic, and then connect to the command line of virtual machine 2 by typing the following command into PowerShell: "ssh [username of virtual machine]@[vm2privateipaddress]. " After typing "yes," enter the password that we created for the administrator account of VM 2.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_372a4facc5734c38adb1fc43aaca6034~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
18. Step 18: While in virtual machine 2's command line, execute the following commands and observe the SSH traffic:
<ul>
  <li>id</li>
  <li>uname -a</li>
  <li>pwd</li>
  <li>ls -lasth</li>
 </ul> 
Then, type "exit" to leave virtual machine 2's command line.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_4a0cbe3701024e32a7a7aa2eb4ef2c53~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 19: Filter for DHCP traffic and execute the command "ipconfig /renew" in PowerShell to force DHCP to assign a new IP address, then observe the traffic.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_ec525f16a24e4da4b72effcda12ebf8a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 20: Filter for DNS traffic, and type "nslookup www.google.com" in PowerShell, then observe the DNS traffic.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_c9aeded7c7f7477b8dbb223e17d5388a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
Step 21: Filter for Remote Desktop Protocol (RDP) traffic and observe the traffic that is already present because of our existing remote desktop connection.
</p>
<br />

<p align="center">💧<b><i>Individually, we are one drop. Together, we are an ocean. ~ Ryunosuke Satoro/b></i>🌊</p>
