# TCP/IP Protocol Architecture
### TCP/IP Architectural Model
1. Application
2. Transport
3. Internet
4. Network access

### Application
Defines the services that applications need. **An interface between software and the network.**

Browser sends an http header to the server. Server returns "OK".
When a particular layer is being communicated on, headers are used to hold information. *Same-layer interactions* use those headers to communicate what they want to do.

### Transport
- Transmission Control Protocol (TCP)
- User Datagram Protocol (UDP)

Provides acknowledgments as an error-recovery feature. This happens going both directions. If acknowledgments were not received successfully, TCP would resend the data.

*Adjacent-layer interactions* work between layers on the same computer. If a higher-layer protocol needs something it can't do, it asks the next lower-layer protocol.

**The Application and Transport layers work the same way regardless of whether the end hosts are on the same LAN or over the Internet.**

### Internet
- Internet Protocol (IP):
  - Defines unique IP addresses for each computer.
  - Defines how a router should forward packets

When IP packets are sent (in either direction) they include:
- IP header (*Source* and *Destination*)
- Transport layer header
- Application layer header
- Any application data

### Network Access
Defines the physical connection medium over which data is transmitted.
- Contains a large number of protocols.

### Data Encapsulation
Encapsulated network data is stored in *frames*, including headers and tailers.
Each layer adds its own header (and sometimes tailer)

##### TCP/IP data sending process
1. Create and encapsulate the application data with any required application layer headers. *(http header and contents)*
2. Encapsulate the data supplied by the application layer inside a transport layer header. *(TCP or UDP)*
3. Encapsulate the data supplied by the transport layer inside an internet layer (IP) header. *(IP is the only protocol available in the TCP/IP network model)*
4. Encapsulate the data supplied by the internet layer inside a network access layer header and tailer. *(This is the only layer that uses both a header and tailer)*
5. Transmit the bits. *(The physical layer encodes a signal onto the medium to transmit the frame)*


- **Segment** - TCP and Data
- **Packet** - IP, TCP Data
- **Frame** - Header, IP, TCP, Data, Tailer
