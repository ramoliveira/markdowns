# Common Ports

## FTP - File Transfer Protocol
Transfers files between systems
* Generic file transfer method
* Not specific to an operating system

> [!INFO]
> TCP/20 (active mode data)
> TCP/21 (control)

* Authenticates with a username and password

Full-featured functionality
LIST, ADD, DELETE, etc.

### SFTP - Secure FTP
* Generic file transfer with security
Encrypted network communication.

* Uses the SSH File Transfer Protocol
TCP/22

* Provides file system functionality
Resuming interrupted transfers, directory listings, remote file removal

* Uses SSH (Port 22)
SSH isn't just for communication

## SSH - Secure Shell
Text-based console communication

Encrypted communication link

> [!INFO]
> TCP/22

## Telnet

* Telnet - Telecommunication Network
TCP/23

* Console access
Similar functionality to SSH

* In-the-clear communication
Not the best choice for production systems

> [!CAUTION]
> There's no encryption that's taking place across the network.

## SMTP - Simple Mail Transfer Protocol

* SMTP - Simple Mail Transfer Protocol
    * Server to server email transfer
    * **TCP/25** -> SMTP using plaintext
    * **TCP/587** -> SMTP using TLS encryption

* Also used to send mail from a device to a mail server
Commonly configured on mobile devices and email clients

* Other protocols are used for clients to receive email
    * IMAP
    * POP3

## DNS - Domain Name System

* Converts names to IP addresses
    * **UDP/53**
    * www.professormesser.com -> 162.159.246.164
    * Large transfers may use **TCP/53**

* These are very critical resources
    * Usually multiple DNS servers are in production

## DHCP - Dynamic Host Configuration Protocol

Automated configuration of IP address, subnet mask and other options
* UDP/67, UDP/68
* Requires a DHCP server
* Server, appliance, integrated into a SOHO router, etc.

Dynamic/pooled
* IP Addresses are assigned in real-lime from a pool
* Each system is given a lease, must renew at set intervals

DHCP reservation
* Addresses are assigned by MAC address in the DHCP server
* Quickly manage addresses from one location.

## TFTP - Trivial File Transfer Protocol

* UDP/69
* Very simple file transfer application
    * Read files and write files
* No authentication
    * Not used on highly secure systems
* Useful when starting a system
    * Transfer configuration files
    * Quick and easy

> [!ABSTRACT]
> Examples of TFTP being used:
> VoiceOver IP device, whenever is plugged in network
> will use DHCP to get an IP. Then, uses TFTP to
> download it's settings.

## HTTP and HTTPS

Hypertext Transfer Protocol
* Communication in the browser
* And by other applications

In the clear or encrypted
* SSL (Secure Sockets Layer), or
* TLS (Transport Layer Security);

|Protocol|Port|Name|Description|
|:-:|:-:|:-|:-|
|HTTP|TCP/80|Hypertet Transfer Protocol|Web server communication|
|HTTPS|TCP/443|HTTP over TLS or SSL|Web server communication with encryption|

## NTP - Network Time Protocol

Switches, routers, firewalls, servers, workstations
* Every device has its own clock
* UDP/123

Synchronizing the clocks becomes critical
* Log files, authentication information, outage details

Automatic updates

Flexible - You control how clocks are updated

Very accurate
* Accuracy is better than 1 millisecond on a local network

## SNMP - Simples Network Management Protocol

Gather statistics from network devices
**UDP/161**

v1 - Original version
* Structured tables
* In-the-clear

v2 - Good step ahead
* Data type enhancements
* Bulk transfers
* Still in-the-clear

v3 - Secure standard
* Message integrity
* Authentication
* Encryption

SNMP traps
* Alerts notifications from network devices
* **UDP/162**

## LDAP/LDAPS

LDAP - Lightweight Directory Access Protocol
* **TCP/389**
* Store and retrieve information in a network directory

LDAPS - LDAP Secure
* A non-standard implementation of LDAP over SSL
* **TCP/636**

## SMB - Server Message Block

> [!HINT]
> Microsoft uses this protocol to data transfer!

Protocol used by Microsoft Windows
* File sharing, printer sharing
* Also called CIFS (Common Internet File System)

Integrated into the operating system
* Access rights integration across systems
* File locking

Direct over **TCP/445** (NetBIOS-less)
* Direct SMB communication over TCP

## Syslog

Standard for message logging
* Diverse systems, consolidated log
* **UDP/514**

Usually a central log collector
* Integrated into the SIEM
* Security Information and Event Manager

You're going to need a lot of disk space
* Data storage from many devices over an extended timeframe

## Databases

Collection of information
* Many different types of data
* One common method to store and query

Structured Query Language (SQL)
* Standard language across database servers
* `SELECT * FROM Customers WHERE Last_Name='Messer';`

* Microsoft SQL Server
- MS-SQL (Microsoft Structured Query Language)
- TCP/1433

## RDP - Remote Desktop Protocol

Share a desktop from a remote location over **TCP/3389**
* Connect to an entire desktop or just an application

Remote Desktop Services on many Windows versions
* Clients for Windows, MacOS, Linux, Unix, iPhone, and others

## SIP - Session Initiation Protocol

Voice over IP (VoIP) signaling
* **TCP/5060** and **TCP/5061**

Setup and manage VoIP sessions
* Call, ring, play busy signal, hang up

Extend voice communication
* Video conferencing
* Instant messaging
* File transfer
* etc.

## ICMP - Internet Control Message Protocol

*"Text messaging"* for your network devices

Another protocol carried by IP
* Not used for data transfer

Devices can request and reply to administrative requests
* *"Hey, are you there?"* / *"Yes, I'm right here."*

Devices can send messages when things don't go well
* That network you're trying to reach is not reachable from here
* *"Your time-to-live expired, just letting you know"*

> [!HINT]
> `ping` command uses ICMP protocol.

## GRE - Generic Routing Encapsulation

The "tunnel" between two endpoints

Encapsulate traffic inside of IP
* Two endpoints appear to be directly connected to each other
* No built-in encryption

## VPN - Virtual Private Network

Encrypted (private) data traversing a public network

**Concentrator**
* Encryption/decryption access device
* Often integrated into a firewall

**Many deployment options**
* Specialized cryptographic hardware
* Software-based options available

### Site-to-site VPN

**Always-on** / *Or almost always*

Firewalls often act as VPN concentrators
* Problably already have firewalls in place

## IPSec - Internet Protocol Security

Security for OSI Layer 3
* Authentication and encryption for every packet

Confidentiality and integrity/anti-replay
* Encryption and packet signing

Very standardized
* Common to use multi-vendor implementations

Two core IPSec protocols:
* Authentication Header - AH
* Encapsulation Security Payload - ESP

### IKE - Internet Key Exchange

Agree on encryption/decryption keys
* Without sending the key across the network
* Builds a *Security Association* - SA

#### Phase I
* Use Diffie-Hellman to create a shared secret key
* UDP/500
* Internet Security Association and Key Management Protocol - ISAKMP

#### Phase II
* Coordinate ciphers and key sizes
* Negotiate an inbound and outbound SA for IPSec

### Transport Mode and Tunnel Mode

**Original Packet**:    IP Header + Data

**Transport Mode**:     IP Header + IPSec Headers + Data + IPSec Trailers 

**Tunnel Mode**:        New IP Header + IPSec Headers + IP Header + Data + IPSec Trailers

### AH - Authentication Header

Authentication Header is a hash of the packet and a shared key
* MD5, SHA-1, or SHA-2 are common
* Adds the AH to the packet Header

**IP Packet with Authentication *(tunnel mode)***: New IP Header + AH Header + IP Header + Data

### ESP - Encapsulation Security Payload

Encrypts the packet
* MD5, SHA-1, or SHA-2 for hash, and 3DES or AES for encryption
* Adds a header, a trailer, and an Integrity Check Value

Encrypted Packet:                       IP Header + Data + ESP Trailer

Authenticated Packet:                   ESP Header + [Encrypted Packet]

**IPSec Datagram with ESP *(tunnel mode)***:  New IP Header + [Authenticated Packet] + Integrity Check Value



