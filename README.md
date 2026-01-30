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

- Windows (Windows 11 Pro)
- Linux (ubuntu 24.04)

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-27 at 5 20 31 AM" src="https://github.com/user-attachments/assets/1e0ab19a-8602-45c1-9271-7db141a440f1" />
</p>
<p>
Step 1: Use Remote Desktop to connect to Virtual Machine (or client computer) by inputing target computer's IP Address and credentials.
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-27 at 5 22 57 AM" src="https://github.com/user-attachments/assets/b8811ca6-1046-4312-bd3a-9c2ef7fe49d2" />
<img width="1728" height="1080" alt="Screenshot 2026-01-27 at 5 45 08 AM" src="https://github.com/user-attachments/assets/eecbd593-2637-4e8a-9ada-2f3f0b5fa4a4" />
</p>
<p>
Step 2: From within remote connection, open Wireshark and start packet capture by accessing ethernet connection (interface showing network traffic).
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-27 at 5 49 28 AM" src="https://github.com/user-attachments/assets/2e81d3bc-9153-4506-a787-fbcd0b94b2f9" />
</p>
<p>
Step 3: Within Wireshark, via searchbar, filter for ICMP traffic only
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 5 35 27 AM" src="https://github.com/user-attachments/assets/0d57499c-6008-41c2-a33f-3083b5f605dc" />
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 5 36 52 AM" src="https://github.com/user-attachments/assets/81f4fd2e-3ac4-4644-a60a-dec6e8ab5b16" />
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 5 37 37 AM" src="https://github.com/user-attachments/assets/500c2ce2-6fee-4d5d-85be-c5777ab4a6d5" />
</p>

<p>
Step 4: Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM by utilizing PowerShell > ping command + Private IP address. Observe ping requests and replies within WireShark.

NOTE: Pinging an IP address checks whether a device can be reached on a network and how fast it responds. It works by sending small test messages and timing the replies, helping identify connection problems like delays, packet loss, or whether the issue is with your computer, the network, or a remote server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
