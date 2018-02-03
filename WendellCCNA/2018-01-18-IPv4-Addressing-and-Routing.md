# Fundamentals of IPv4 Addressing and Routing
- **IP routing:** LANs and WANs forward the packets from routers and hosts.
- **IP addressing:** Groups addresses and identifies a packet's source and destination.
- **IP routing protocol:** Dynamically learns address groups to help routers know where to route packets.

### Overview of Network Layer Functions
IP routes data (as packets) from source to destination, with no concern for the physical transmission. This is handled instead by lower TCP/IP layers. The network layer directs packets, even over different LAN and WAN links.

### Network Layer Routing Logic
Hosts work together to achieve IP routing.

### Routing Protocols
Hosts need to know the IP address of the default gateway. Routers need to know routes to forward packets to each network and subnet.

### IPv4 addressing
#### Rules for IP addresses
Devices communicating over TCP/IP need IP addresses. IP addresses are 32-bit numbers written in dotted-decimal notation. Every 8 bits of the address is written in sequence. Each has 4 decimal octets (bytes) -- 0-255 inclusive.

### Rules for Grouping IP Addresses
- All IP addresses in the same group must not be separated from each other by a router.
- IP addresses separated fro each other by a router must be in different groups.
