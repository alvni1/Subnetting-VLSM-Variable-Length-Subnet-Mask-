<h1>Subnetting Variable Length Subnet Mask (VLSM) </h1>

<h2>Description</h2>
A subnet mask is a 32-bit number that divides an IP address into network and host portions, facilitating the creation of subnetworks (subnets) within a larger network. Subnetting enhances network performance and security by reducing broadcast domains and enabling efficient IP address management. A Local Area Network (LAN) is a network that connects devices within a limited geographic area, such as an office or building. LANs are crucial for enabling high-speed communication and resource sharing among connected devices. Subnetting within a LAN allows for logical segmentation, improving network management and performance by isolating traffic and reducing congestion.


In the provided network configuration, four Local Area Networks (LANs) are designed with specific subnetting to accommodate varying host requirements.

LAN2, requiring 64 hosts, is assigned a /25 prefix, resulting in a subnet mask of 255.255.255.128. The network address is 192.168.5.0, with a broadcast address of 192.168.5.127. Router R1's interface g0/1 is configured with the last usable IP address, 192.168.5.126, while PC1 is assigned the first usable address, 192.168.5.1, with R1's IP as its default gateway.

LAN1, needing 45 hosts, utilizes a /26 prefix, yielding a subnet mask of 255.255.255.192. Its network address is 192.168.5.128, and the broadcast address is 192.168.5.191. The first and last usable IP addresses are 192.168.5.129 and 192.168.5.190, respectively.

LAN3 and LAN4 are both allocated a /28 prefix, providing 16 IP addresses each. LAN3's network address is 192.168.5.192, with a broadcast address of 192.168.5.207, and usable IP addresses ranging from 192.168.5.193 to 192.168.5.206. LAN4 starts at 192.168.5.208, has a broadcast address of 192.168.5.223, and usable addresses from 192.168.5.209 to 192.168.5.222.

For point-to-point connections between routers, a /30 prefix is employed, offering two usable IP addresses. Typically, the first usable address is assigned to one router, and the last to the connecting router, facilitating efficient inter-router communication.

After configuring static routes on the routers, direct connectivity between PCs across the network is established, enabling successful communication. During troubleshooting, it was noted that an incorrect subnet mask on LAN4's router interface g0/1 prevented PC4 from being reachable. Correcting this configuration allowed all PCs to communicate effectively.

<h2>Things Learned/Troubleshooting</h2>

During troubleshooting, an incorrect subnet mask on LAN4's router interface g0/1 prevented PC4 from being reachable. Correcting this configuration allowed all PCs to communicate effectively.

<h2>Languages and Utilities Used</h2>

- <b>Cisco Command Line Interface</b> 

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b>

<h2>Program walk-through:</h2>

Static IP routes are added to R1 to allow connectivity to both LAN3 and LAN4. In this specific scenario, the next-hop address is R2. 
![Screenshot 2025-01-18 022041](https://github.com/user-attachments/assets/692c9927-8b33-4b55-944f-46788261cfde)

R1's point-to-point link of interface g0/0/0 is configured with the first usable address within the 192.168.5.224/30 subnetmask. 
![Screenshot 2025-01-18 021714](https://github.com/user-attachments/assets/aa9930a9-796e-478d-b3ef-4378787f0838)

With a broadcast address of 192.168.5.127 and a network address of 192.168.5.0, LAN 2's g0/1 interface is configured with the last usable address and the PC within this LAN is configured with the first usable address. 
![Screenshot 2025-01-17 235110](https://github.com/user-attachments/assets/473855c2-aaa6-42f9-ad09-18b5b017e70e)

With a broadcast address of 192.168.5.207 and a network address of 192.168.5.192, LAN 3's g0/0 interface is configured with the last usable address and the PC within this LAN is configured with the first usable address. 
![Screenshot 2025-01-18 012231](https://github.com/user-attachments/assets/926721f2-692e-4a6a-ba34-527949689aab)

With a broadcast address of 192.168.5.223 and a network address of 192.168.5.208, LAN 4's g0/1 interface is configured with the last usable address and the PC within this LAN is configured with the first usable address. 
![Screenshot 2025-01-18 020900](https://github.com/user-attachments/assets/4f7d3efe-1fa4-44c2-bb76-6b8a3fea6fce)

R2's point-to-point link of interface g0/0/0 is configured with the last usable address within the 192.168.5.224/30 subnetmask. 
![Screenshot 2025-01-18 021554](https://github.com/user-attachments/assets/6264c29f-a13d-4ef0-9f1a-fd097a997f71)

Static IP routes are added to R2 to allow connectivity to both LAN1 and LAN2. In this specific scenario, the next-hop address is R1. 
![Screenshot 2025-01-18 022219](https://github.com/user-attachments/assets/5f028bc5-ccaa-4ddf-bb1e-f9151eddb58c)

PC1 pings PC3 and PC4 to ensure connectivity and that all routes were properly configured.
![Screenshot 2025-01-20 212713](https://github.com/user-attachments/assets/ff8c8a4b-0de9-4875-a4f9-01a899fc9c11)

PC2 pings PC3 and PC4 to ensure connectivity and that all routes were properly configured.
![Screenshot 2025-01-20 204619](https://github.com/user-attachments/assets/828ad1b8-0cfd-4b38-9e41-231319d2f9da)

Troubleshooting: LAN4 had the wrong subnet mask configured on the router for PC4. The destination host was unreachable when trying to ping PC4. Once I deleted the first configuration for g0/1 and re-entered it, the other computers were able to ping PC4. 
![Screenshot 2025-01-20 212730](https://github.com/user-attachments/assets/820107a2-97b2-4e11-bac0-be81d9c3b95e)
