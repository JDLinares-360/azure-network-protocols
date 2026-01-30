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

<h2>Configuring a Firewall [Network Security Group]</h2>

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 5 52 19 AM" src="https://github.com/user-attachments/assets/c52e45d3-748e-4ec2-b9f6-f50f0d7f0d65" />
</p>
<p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM via PowerShell and the ping command + private IP Address + -t
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 03 43 AM" src="https://github.com/user-attachments/assets/be34e29c-939f-47c3-9a37-bb238de8e277" />
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 11 32 AM" src="https://github.com/user-attachments/assets/36c51355-7af0-4205-9818-ce3d5e95c7e5" />
</p>
<p>
Navigate to linux-vm's NSG/Firewall and disable incoming (inbound) ICMP traffic. Azure Portal > VM > Network Settings > Rules > Add inbound security rule > Protocol = ICMPv4, Action = Deny, Priority = 290 (New security rule will be evauluated first)
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 13 03 AM" src="https://github.com/user-attachments/assets/5e4b49e8-cd88-4e7f-b920-583bab0034d7" />
</p>
<p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity. Request will "time out" due to the new inbound security rule/firewall blocking them.
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 19 18 AM" src="https://github.com/user-attachments/assets/3e41f26b-ce0a-4c49-8ede-474d05d52f6b" />
</p>
<p>
Re-enable ICMP traffic for the Network Security Group your linux VM by deleting the new rule 
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 19 57 AM" src="https://github.com/user-attachments/assets/d50bb074-22fc-4dd2-9267-6392d6a3000d" />
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 6 22 32 AM" src="https://github.com/user-attachments/assets/7cb79cbe-189a-4fcd-999a-a1f145852098" />
</p>
<p>
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working) and Stop the ping activity (PowerShell, Control+c)
</p>
<br />

<h3>(Observe SSH Traffic)</h3>

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 10 32 26 AM" src="https://github.com/user-attachments/assets/ed787d3f-e801-4ef3-b7c6-1759c27de054" />
</p>
<p>
Log back into the windows-vm, back in Wireshark, start a packet capture, filter for SSH traffic only
</p>
<br />

<p>
<img width="1728" height="1080" alt="Screenshot 2026-01-30 at 10 32 26 AM" src="https://github.com/user-attachments/assets/ed787d3f-e801-4ef3-b7c6-1759c27de054" />

</p>
<p>
From your Windows VM, “SSH into” your Ubuntu/Linux Virtual Machine (via its private IP address)
</p>
<br />
