VirtualBox Lab Assignment
Objective
Install and configure Oracle VirtualBox hypervisor, create a virtual machine using an Ubuntu ISO image, and verify successful installation.

Tools Used
Hypervisor: Oracle VirtualBox 7.2.16

Guest OS: Ubuntu 26.04 LTS (Desktop)

Host OS: Windows

Lab Steps and Screenshots
Step 1: Download VirtualBox and Ubuntu ISO
Downloaded VirtualBox 7.2.16 from official website

Downloaded Ubuntu 26.04 LTS Desktop ISO (5.9GB, AMD64 architecture)

https://1.jpeg
https://2.jpeg

Step 2: Create Virtual Machine
Configured VM with the following specifications:

Name: Ubuntu 26.04

Type: Linux

Subtype: Ubuntu (64-bit)

ISO Image: F:\ubuntu-26.04-desktop-amd64.iso

Storage Folder: C:\Users\amans\VirtualBox VMs

https://3.jpeg

Step 3: VM Configuration Details
System Settings
Base Memory (RAM): 4096 MB (4 GB)

Processors: 3 CPU cores

Boot Order: Hard Disk, Optical, Floppy

Acceleration: Nested Paging, KVM Paravirtualization

Pointing Device: USB Tablet

https://4.jpeg
https://5.jpeg
https://6.jpeg
https://7.jpeg

Display Settings
Video Memory: 64 MB

Graphics Controller: VBoxVGA

Monitor Count: 1

Scale Factor: 100%

https://8.jpeg
https://9.jpeg

Storage
Controller: SATA

Storage Device: Aman_s Cloud Lab.vdi (25.00 GB)

Optical Drive: Empty (ISO attached for installation)

Network
Adapter 1: Intel PRO/1000 MT Desktop (NAT)

USB
Controller: OHCI + EHCI

Step 4: Guest OS Installation & Verification
The VM was successfully started and Ubuntu 26.04 was installed. After installation, the following system updates were performed:

System Update:

bash
sudo apt update
Install Build Tools:

bash
sudo apt install -y build-essential linux-headers-$(uname -r)
https://10.png

Verification Results:

Package list updated successfully

build-essential already installed

Linux headers (7.0.0-14-generic) already installed

313 packages available for upgrade

https://11.png

VM Configuration Summary
Component	Configuration
OS Type	Ubuntu (64-bit)
RAM	4096 MB
Processors	3
Storage	25 GB (VDI)
Video Memory	64 MB
Graphics Controller	VBoxVGA
Network	NAT
USB	OHCI + EHCI
Audio	ICH AC97
Acceleration	Nested Paging, KVM
Challenges Faced & Solutions
Issue: "Invalid settings detected" warning in VirtualBox settings

Solution: The warning appeared during configuration but was resolved after finalizing all settings. This is common when making multiple changes simultaneously.

Verification Checklist
☑ VirtualBox 7.2.16 installed
☑ Ubuntu 26.04 ISO downloaded
☑ VM created with proper specifications
☑ VM boots successfully
☑ sudo apt update works
☑ Build tools and kernel headers installed
☑ System running without errors
Conclusion
The installation of VirtualBox hypervisor and Ubuntu 26.04 VM was completed successfully. The VM is fully functional with 4GB RAM, 3 CPU cores, and 25GB storage. The guest OS installation completed without issues, and the required development tools were installed, verifying that the VM environment is ready for further development work.

References
VirtualBox Documentation

Ubuntu 26.04 LTS

Submission Details
Student: Debraj

Date: August 20, 2026
