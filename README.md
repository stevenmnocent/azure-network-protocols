<p align="center">
<img src="https://static.wixstatic.com/media/2ebf04_4302f0f9efbd490a84e66d0ea2a414bd~mv2.png" alt="Traffic Examination"/>
</p>
<br />

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://youtu.be/O3ISo0YCi5Q)

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
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_74ce579cb3554e9e9a00af755dd07e7a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
1. Create a new resource group within Microsoft Azure.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_61e5bacfe40d4d22af40882a361f5fce~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
2. Create an Azure virtual machine (VM) running Windows 10 Pro, Version 21H2.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_96bbdd6333ea4f8d8403f9420f954a46~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
3.Create a username and password for the administrator account, and then create the VM.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_04cca0787a69459190356b6feff09069~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
4. Create a second virtual machine running Ubuntu Server 20.04 LTS, create a username and password for the administrator account and add it to the same resource group and virtual network as the first VM.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cd1617d3c2e749da885e05752055a236~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
5. Remote desktop connection into the first virtual machine.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_b462864732e1497eaf73b416bec56483~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
6. Go to https://wireshark.org/download.html in Microsoft Edge and download version 4.0.4.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_10e47a6adb6f449588dea6f9a8438d50~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
7. Install Wireshark with default install settings.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_301150f264f8472793827b9f7ac8a87b~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
8. Launch Wireshark and click ethernet → Blue Wireshark icon to start capturing packets.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f1e2b1d34bdb4ac38a85c67a08642a99~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
9. Observe the traffic and then filter for ICMP traffic.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_986726791478472a873a8e0bc1b9c6e8~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
10. Open Windows PowerShell and ping the second virtual machine running Ubuntu Server’s private IP address and observe the traffic.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_373ac50481ce473ea35273fa68c9f533~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
11. Non-stop ping the second virtual machine with -t command, and then we are going to proceed to deny ICMP traffic from Azure for virtual machine 2.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_8967649fbb0d491a802599ce03260a23~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
12. Go to network security groups → The second virtual machine → Inbound security rules → Add.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_c953682793ce46f69b62ede583aa38b9~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
13. Keep setting the same but change the protocol to ICMP, click Deny for action and set the priority to 299, then click add.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_13595cfa7ff042b6913e596de32dbe31~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
14. Observe how ICMP Traffic is halted because of the changes we made to block ICMP.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_4b486f9531a8465ba31f4f6043daad20~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
15. Go back to Inbound security rules in Azure and allow ICMP Traffic by clicking allow under action and click save.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_20c36a1818e04221ba47a4771bbecf95~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
16. Observe how we are beginning to receive replies again for ICMP Traffic, then click Ctrl + C to stop the non-stop ping.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_fa916015d0ed470aba66562c8de14edb~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
17. Filter for SSH traffic, then connect into virtual machine 2’s command line by typing in the following command in PowerShell: ssh [username of virtual machine]@[vm2privateipaddress] → Then type yes → Then enter VM 2’s password that we created for the administrator account.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_372a4facc5734c38adb1fc43aaca6034~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
18. Once in virtual machine 2’s command line type in following commands and observe SSH Traffic:
- id
- uname -a
- pwd
- ls -lasth
Then type in Exit, to leave virtual machines 2’s command line.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_4a0cbe3701024e32a7a7aa2eb4ef2c53~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
19. Filter for DHCP Traffic, and type in ipconfig /renew in PowerShell to force DHCP to reassign a new IP address and observe the traffic.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_ec525f16a24e4da4b72effcda12ebf8a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
20. Filter for DNS traffic, and type in nslookup www.google.com in PowerShell, then observe the DNS traffic.
</p>

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_c9aeded7c7f7477b8dbb223e17d5388a~mv2.png" height="80%" width="80%" alt="Network Security Groups (NSGs) and Inspecting Network Protocols"/>
</p>
<p>
21. Filter for Remote Desktop Protocol (RDP) and observe the traffic already present because we are currently using a remote desktop connection.
</p>
<br />

<p align="center"><b><i>🙌💥People may hear your words, but they feel your attitude. ~ John C. Maxwell🙌💥</b></i></p>
