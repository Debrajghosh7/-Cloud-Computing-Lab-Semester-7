Linux VM-to-VM Network Connectivity Test

📌 Overview

This experiment demonstrates basic network connectivity between two Ubuntu Linux Virtual Machines running in VirtualBox. The ip a command was used to identify the network interface and IP address of each VM, followed by the ping command to verify communication between them.

🎯 Objective

Identify the IP address of each Ubuntu VM.

Check the status of the network interface.

Test connectivity between two virtual machines.

Verify packet delivery and network latency using ICMP ping.

🛠️ Environment

Component

Details

Host/Hypervisor

Oracle VirtualBox

Guest OS

Ubuntu Linux

Network Interface

enp0s3

Network Type

VirtualBox network

Testing Tool

ping

IP Network

10.0.2.0/24

🖥️ VM 1

The first Ubuntu VM was configured with:

Interface : enp0s3 IP Address: 10.0.2.15/24

The interface was verified using:

ip a

Connectivity to the second VM was tested with:

ping 10.0.2.4

Result

8 packets transmitted, 8 received, 0% packet loss rtt min/avg/max/mdev = 0.298/0.584/0.787/0.140 ms

This confirms that VM 1 successfully communicated with VM 2.

🖥️ VM 2

The second Ubuntu VM was configured with:

Interface : enp0s3 IP Address: 10.0.2.4/24

The interface was verified using:

ip a

Connectivity to the first VM was tested with:

ping 10.0.2.15

Result

6 packets transmitted, 6 received, 0% packet loss rtt min/avg/max/mdev = 0.339/0.597/0.825/0.190 ms

This confirms that VM 2 successfully communicated with VM 1.

📊 Connectivity Summary

Test

Source VM

Destination

Packets Lost

Status

Ping Test 1

10.0.2.15

10.0.2.4

0%

✅ Successful

Ping Test 2

10.0.2.4

10.0.2.15

0%

✅ Successful

🔧 Commands Used

Display network configuration
ip a

This command displays the available network interfaces, their state, MAC addresses, IPv4 addresses, and IPv6 addresses.

Test connectivity
From VM 1:

ping 10.0.2.4

From VM 2:

ping 10.0.2.15

Press Ctrl + C to stop the continuous ping test and display the statistics.

📸 Screenshots

VM 1 — IP Configuration and Ping Test

VM 2 — IP Configuration and Ping Test

Note: Keep 1.png and 2.png in the same directory as this README.md when uploading the project to GitHub.

✅ Conclusion

The two Ubuntu virtual machines were successfully connected through the VirtualBox network. Both VMs were able to reach each other using ICMP ping, with 0% packet loss in both tests. This verifies successful basic network communication between the virtual machines.

👨‍💻 Author

Debraj Ghosh B.Tech Computer Science & Engineering Adamas University
