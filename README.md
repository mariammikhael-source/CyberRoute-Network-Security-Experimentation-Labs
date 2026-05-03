🔐 Network Security Labs

📘 Lab 1: Packet Sniffing, Spoofing, and Traceroute

In this lab, I completed a series of tasks within the AUC CyberRange environment focusing on fundamental network security concepts, including packet sniffing, spoofing, and traceroute analysis. Below is a breakdown of the tasks performed:

🔍 Task 1: Packet Sniffing

I passively captured and analyzed network traffic using tcpdump and Wireshark, applying advanced filtering techniques to isolate specific protocols and traffic patterns:

Captured ICMP packets (ping traffic) to analyze request/response behavior
Filtered TCP packets targeting port 23 (Telnet) to inspect application-layer communication
Isolated traffic within the local subnet to study internal network flows

These tasks enabled detailed inspection of packet headers, flags, and payloads, providing insight into protocol behavior and traffic monitoring under different privilege levels.

🛰️ Task 2: Packet Spoofing

I explored packet injection and IP spoofing techniques using Scapy to simulate adversarial behavior:

Crafted packets with forged source IP addresses
Transmitted spoofed packets and captured responses to evaluate network behavior
Tested multiple spoofing scenarios to analyze detection limitations and trust-based vulnerabilities

This task demonstrated how attackers can exploit weaknesses in IP-based authentication mechanisms.

🌐 Task 3: Traceroute Analysis

I implemented a custom traceroute mechanism to actively map network paths:

Sent ICMP packets with incrementally increasing TTL values
Captured ICMP Time Exceeded responses from intermediate routers
Reconstructed the full network path hop-by-hop
Compared results with the standard traceroute tool to validate accuracy

This task provided hands-on experience in network path discovery and reconnaissance techniques.

📘 Lab 2: ICMP Redirect Attack and Routing Manipulation

In this lab, I performed multiple tasks demonstrating how ICMP redirect messages can be exploited to manipulate routing behavior and enable Man-in-the-Middle (MITM) attacks.

🛰️ Task 1: Launching ICMP Redirect Attack

I configured a containerized lab environment and executed an ICMP redirect attack:

Disabled default ICMP protections in the victim container via docker-compose configuration
Crafted and sent ICMP Redirect packets to the victim using Scapy
Redirected traffic destined for 192.168.60.5 to a malicious router (10.9.0.111)

Observations:

The routing table remained unchanged, but the routing cache was modified
Verified changes using ip route show cache
Used mtr to confirm that traffic was redirected through the malicious node
🌍 Task 1.B: Redirect to a Remote Machine

I extended the attack to target an external host:

Modified the attack to redirect traffic toward a remote IP address
Observed that the attack was ineffective across network boundaries

Conclusion:
Routing manipulation via ICMP redirect is generally limited to local networks due to modern routing constraints and security mechanisms.

🚫 Task 1.C: Redirect to a Non-Existing Machine

I simulated an attack using an invalid next-hop address:

Sent ICMP redirect packets pointing to a non-existent host
Observed temporary updates in the routing cache

Outcome:

Packet delivery failed due to unreachable destination
Demonstrated the instability and temporary nature of routing cache manipulation
⚙️ Task 1.D: Analyzing docker-compose.yml Configuration

I analyzed the network configuration of the malicious router container:

Examined parameters controlling routing behavior:
ip_forward (packet forwarding)
send_redirects (ICMP redirect capability)

