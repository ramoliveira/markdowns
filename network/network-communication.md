# Network Communication

## Unicast (1 -> 1)

One emitter and one receiver. *One-to-one*.
Used in IPv4 and IPv6.
Doesn't scale for real-time streaming media.

> [!EXAMPLE] 
> * Accessing a website through HTTP and HTTPS
> * File transfering

## Broadcast (1 -> All)

One emitter and all devices in a local network. *One-to-all (LAN)*.
Only works inside of local network.
Can create a brodcast storm (excess of broadcast running through network).
Used in IPv4. Whenever need to be used in IPv6, is used multicast.

> [!EXAMPLE]
> ARP asking: "Who has this IP?"

> [!QUESTION]
> **Why there is no IPv6?**
> Broadcast interrupts all devices. Generates noises. Doesn't scale.

> [!QUESTION]
> **What is the interruption caused by Broadcast?**
> Whenever a packet is sent to all devices in LAN. Each network board has to process this packet. OS must stack this packet in order of deciding if should ignore it.
> 
> This can lead to CPU and RAM usage increase.

> [!QUESTION]
> **What is the noise caused by Broadcast?**
> As said before, whenever a packet is sent to all devices in LAN. Every device receives it. If just 1 device answers it, other N-1 devices processed this packet for nothing.

### **How does Broadcast don't scale?**

#### Small Scenary
* 10 devices
* 1 broadcast

10 devices easily processing packets

#### Medium Scenary (enterprise)
* 500 devices
* DHCP, ARP, discovery happening all the time

Thousands of broadcasts per minute. 500 devices processing each one.

#### Bigger Scenary (datacenter / campus)
* 10.000+ devices

Network processing weights heavily. Switches get overloaded. Starts to happen broadcast storm.

## Multicast (1 -> Group)

One emitter and multiple receivers. *One-to-many-of-many*.
Is very specialized. Difficult to scale across large networks.
Used in IPv4 and IPv6. Extensively used in IPv6.
Must subscribe in order of receiving packets.
It's better than unicasting multiple destinies.

> [!EXAMPLE]
> * Multimedia delivery
> * Stock exchanges
> * Dynamic routing updates

## Anycast (1 -> Closest)

One emitter and closest receiver (server). *One-to-one-of-many*.
Multiple server can share the same IP address. So packets sent to an anycast address are delivered to the closest interface.
* Can look like any other unicast address.
Used in IPv4 and IPv6.

> [!EXAMPLE]
> Google Public DNS (8.8.8.8)
> Cloudflare (1.1.1.1)

