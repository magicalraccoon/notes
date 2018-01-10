# OSI Reference Model
### Open System Interconnection *reference* model
Now used as a reference for discussing other protocols.
1. Application
2. Presentation
3. Session
4. Transport
5. Network
6. Data Link
7. Physical

Although similar, OSI layers do not exactly line up with TCP/IP layers.

### OSI Layers and Functions
**Layer 7 - *Application*** - Interface between software and and applications that require outside communication.

**Layer 6 - *Presentation*** - Define and negotiate data formats. Includes encryption.

**Layer 5 - *Session*** - Defines and manages sessions. Controls bidirectional messages that can alert if not all are completed.

**Layer 4 - *Transport*** - Relates to data delivery to other computers.

**Layer 3 - *Network*** - Manages addressing, routing (data forwarding), and path determination (best route for routing).

**Layer 2 - *Data Link*** - Determines when a device can send data over a particular medium. Also defines the format of headers and tailers.

**Layer 1 - *Physical*** - Exclusively the physical transmission medium.

*Fun mnemonic: Please Do Not Take Sausage Pizzas Away (Layers 1 to 7)*

### OSI Encapsulation Terminology
Lower layers encapsulate the higher layer's within a header.

Protocol Data Unit (PDU) - *bits that include headers and tailers, as well as the encapsulated data. Can be used like L3PDU (Layer 3 PDU).*
