# SSH-Configuration-on-Cisco-IOS-Device
In this project, I demonstrated how to secure remote device access using SSH on a Cisco IOS router. The network consists of Router 1 (R1), Switch 1 (S1), and an Admin PC, connected in a basic topology to simulate a secure remote management scenario.



🧠 Project Objectives
Configure the Gateway_Router as a DHCP relay agent using the ip helper-address command.

Ensure DHCPDISCOVER messages from clients on the 172.16.20.0/24 network are forwarded to a remote DHCP server on the 192.168.100.0/24 network.

Successfully assign IP addresses to client PCs using dynamic addressing.

Verify inter-network connectivity and ARP resolution to prevent initial DHCP failure in Packet Tracer simulation.

🌐 Network Topology Overview
arduino
Copy
Edit
[Client PCs]
    |
[Gateway_Router]
 | G0/0: 172.16.20.1/24   (Client LAN)
 | G0/2: 192.168.100.1/24 (DHCP Server LAN)
    |
[DHCP Server: 192.168.100.25]
🧾 Key Configuration Steps
🔹 Step 1: Configure the Gateway Router as a DHCP Relay
bash
Copy
Edit
Gateway_Router# configure terminal
Gateway_Router(config)# interface gigabitEthernet 0/0
Gateway_Router(config-if)# ip helper-address 192.168.100.25
This command enables DHCP relay functionality on the client-facing interface by forwarding DHCP broadcasts (e.g., DHCPDISCOVER) as unicast to the specified DHCP server.

🔹 Step 2: Verify Network Connectivity
bash
Copy
Edit
Gateway_Router# ping 192.168.100.25
A successful ping ensures the router can reach the DHCP server, which also pre-populates the ARP table to avoid the known Packet Tracer delay bug that drops the first DHCP attempt due to unresolved MAC addresses.

🔹 Step 3: Enable DHCP on Client Hosts
On each PC:

Go to Desktop > IP Configuration.

Click DHCP to request an IP address from the DHCP server.

✅ Project Outcome
Both client PCs received valid IP addresses from the DHCP server across different subnets.

The router correctly relayed DHCP requests, validating the helper-address functionality.

Connectivity between the clients and the server was successfully tested using ping and ARP verification.

📘 Skills Demonstrated
DHCP relay agent configuration using ip helper-address

Inter-subnet routing and ARP behavior in Cisco environments

Practical debugging of DHCP timeouts in simulation tools (Packet Tracer quirk)

End-to-end testing of dynamic IP assignment over routed networks

<b>Project Video Demo<b/> https://youtu.be/V-s7itV1MWM
