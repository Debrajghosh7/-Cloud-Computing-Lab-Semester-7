
Mininet Network Topology Experiments

👤 Author: DEBRAJ GHOSH 🎓 Bachelor of Technology (B.Tech) in Computer Science and Engineering 🏫 Adamas University

This repository documents two basic Software-Defined Networking (SDN) lab experiments performed using Mininet, a network emulator that creates virtual hosts, switches, and links for testing and prototyping network topologies.

🖥️ Environment OS: Ubuntu (VirtualBox VM — AmanCloud) Tool: Mininet 2.3.0 Switch backend: Open vSwitch (OVS Bridge — used since no OpenFlow controller was specified) Interface: Mininet CLI 📦 Installation

Mininet was installed via APT along with its dependencies (Open vSwitch, netifaces, sortedcontainers, etc.):

bash sudo apt install mininet -y

Verify installation:

bash mn --version

2.3.0
Topology 1 — Single Switch with 2 Hosts

A minimal star topology with one switch (s1) connected to two hosts (h1, h2).

Command bash sudo mn --topo single,2 Topology Diagram h1 h2 \ / \ / [ s1 ] Steps Performed Started Mininet with the single,2 topology (1 switch, 2 hosts). Verified nodes and links: mininet> nodes available nodes are: h1 h2 s1

mininet> links h1-eth0<->s1-eth1 (OK OK) h2-eth0<->s1-eth2 (OK OK) Checked IP configuration on each host (h1 ip addr, h2 ip addr): Host Interface MAC Address IP Address h1 h1-eth0 ea:9a:84:80:30:96 10.0.0.1/8 h2 h2-eth0 42:be:d6:1f:16:3c 10.0.0.2/8 Ran connectivity tests: mininet> h1 ping -c 4 h2 4 packets transmitted, 4 received, 0% packet loss rtt min/avg/max/mdev = 0.075/0.148/0.348/0.115 ms

mininet> pingall *** Results: 0% dropped (2/2 received) Result

✅ Full connectivity confirmed between h1 and h2 through switch s1.

Topology 2 — Single Switch with 4 Hosts

Extends Topology 1 to a star topology with one switch (s1) and four hosts (h1–h4).

Command bash sudo mn --topo single,4 Topology Diagram h1 h2 h3 h4 \ \ / / \ \ / / [ s1 ] Steps Performed Started Mininet with the single,4 topology (1 switch, 4 hosts). Verified nodes and links: mininet> nodes available nodes are: h1 h2 h3 h4 s1

mininet> links h1-eth0<->s1-eth1 (OK OK) h2-eth0<->s1-eth2 (OK OK) h3-eth0<->s1-eth3 (OK OK) h4-eth0<->s1-eth4 (OK OK) Checked IP configuration on each host: Host Interface MAC Address IP Address h1 h1-eth0 d2:fc:e7:9f:24:52 10.0.0.1/8 h2 h2-eth0 aa:39:f8:39:f5:14 10.0.0.2/8 h3 h3-eth0 8e:0e:f0:aa:eb:cb 10.0.0.3/8 h4 h4-eth0 ce:f1:89:34:da:ce 10.0.0.4/8 Ran individual ping tests between host pairs (h1↔h2, h1↔h3, h2↔h4) — all successful with 0% packet loss. Ran full mesh connectivity test: mininet> pingall h1 -> h2 h3 h4 h2 -> h1 h3 h4 h3 -> h1 h2 h4 h4 -> h1 h2 h3 *** Results: 0% dropped (12/12 received) Inspected network and routing tables: mininet> net h1 h1-eth0:s1-eth1 h2 h2-eth0:s1-eth2 h3 h3-eth0:s1-eth3 h4 h4-eth0:s1-eth4 s1 lo: s1-eth1:h1-eth0 s1-eth2:h2-eth0 s1-eth3:h3-eth0 s1-eth4:h4-eth0

mininet> h1 route Destination Gateway Genmask Flags Iface 10.0.0.0 0.0.0.0 255.0.0.0 U h1-eth0 Result

✅ Full mesh connectivity confirmed across all 4 hosts (12/12 pings received, 0% packet loss).

🧹 Cleanup

After each experiment, Mininet's internal state was cleared to avoid conflicts in subsequent runs:

bash sudo mn -c

This removes leftover controllers, switches, links, OVS datapaths, and stale network namespaces.

📝 Useful Mininet CLI Commands Reference Command Description nodes List all nodes (hosts + switches) in the topology links Show link status between nodes net Display network connections ip addr Show IP/MAC configuration of a host route Show routing table of a host

ping -c 4
Ping between two specific hosts pingall Test connectivity between all host pairs exit Exit the Mininet CLI sudo mn -c Clean up Mininet state 📌 Notes Since no OpenFlow controller was specified, Mininet automatically fell back to using an OVS Bridge (standalone L2 learning switch mode). All hosts were assigned IPs from the 10.0.0.0/8 subnet automatically by Mininet. Both topologies achieved 0% packet loss, confirming correct switch forwarding behavior. 📚 References Mininet Official Documentation Mininet Walkthrough 👤 Author
Name Aman Srivastava Degree Bachelor of Technology (B.Tech) — Computer Science and Engineering University Adamas University

This project was created as part of practical learning in Cloud Computing using Mininet.
