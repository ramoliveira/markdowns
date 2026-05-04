# OSI

|Osi Model Layers|
|:-:|
|Application|
|Presentation|
|Session|
|Transport|
|Network|
|Data Link|
|Physical|

# Layers

* **Application Layer**:
    Application layer is where network applications and their application-layer protocols reside. The Internet's application layer includes many protocols:
    * HTTP protocol (Web document request and transfer);
    * SMPT (e-mail messages); and
    * FTP (transfer files).

    > [!HINT] 
    > *Application layer* information packet's are known as messages.

    > [!INFO]
    > Presentation and Session layers are usually presented as part of Application Layer, in other internet models.
    > *Presentation layer* is responsible for encrypting and decrypting, character encoding.
    > *Session layer* is responsible for tokens and authentication.

* **Presentation Layer**:
    Application encryption and decryption.

    * SSL/TLS

* **Session Layer**:
    * Control protocols
    * Tunneling protocols

* **Transport Layer**:
    Transports application-layer information between application endpoints. In the internet there are two transport protocols:

    * *TCP* (Trasmission Control Protocol): Connection-oriented service. Garanteed delivery of application-layer messages to the destination.
        > [!NOTE]
        > TCP also breaks long messages into shorter segments and provider a congestion-control mechanism.

    * *UDP* (User Datagram Protocol): Connectionless service. Providers no reliability, no flow control, and no congestion control.

    > [!HINT] 
    > *Transport layer* packet's are known as segments.

* **Network Layer**:
    * Moves packets from one host to another. Receives a destination address and a transport-layer segment. 
    * Then deliveries the segment to the transport layer in the destination host.
    * Network layer is made of IP protocol (there is only one) and routing protocols.
    
    > [!NOTE]
    > Example of routing protocols: 
    >   * **Intra-domain**: 
    >       * RIP (Routing Information Protocol);
    >       * OSPF (Open Shortest Path First); 
    >       * IS-IS (Intermediate System to Intermediate System).
    >   * **Inter-domain**: BGP (Border Gateway Protocol).

    > [!HINT] 
    > *Network layer* packet's are known as datagrams.

* **Data Link Layer**:
    To move a packet from one node (host or router) to the next node in the route, the network layer relies on the services of the link layer.

    * Data Link Control (DLC) protocols
        - MAC (Media Access Control) address on Ethernet
    
    ## Other topics in Data Link Layer
    * Extended Unique Identifier (EUI-48, EUI-64)
    * Switches

   > [!NOTE]
   > Examples of link-layer protocols:
   >    * Ethernet;
   >    * WiFi;
   >    * Cable access network's DOCSIS protocol;
   >    * PPP.

   > [!HINT]
   > *Link layer* packet's are knwon as frames.


# How data is transformed

Application Layer -> Transport Layer -> Network Layer -> Data Link Layer -> Physical Layer
Information       -> Messages        -> Segments      -> Datagrams       -> Frames

