# IPv4 Addressing

## IP Address 
* Example: 192.168.1.165.
* Every device needs a unique IP address

## Subnet mask
* Example: 255.255.255.0.
* Is used by local device to determine what subnet it's on
    * The subnet mask isn't (usually) transmitted across the network
    * You'll ask for the subnet mask all the time

## Default gateway 
* Example: 192.168.1.1
* The router that allows you to communicate outside of your local subnet
* The default gateway must be an IP address on the local subnet

## Loopback address
* It's an address to yourself
* Ranges from 127.0.0.1 through 127.255.255.254
* An easy way to self-reference (ping 127.0.0.1)

## Reserved addresses
* Set aside for future use or testing
* 240.0.0.1 through 254.255.255.254
* All "Class E" addresses

## Virtual IP Addresses (VIP)
* Not associated with physical network adapter
* Virtual machine, internal router address

## IPv4 Addresses

Internet Protocol version 4
* Is an OSI Layer 3 address

192      168      1        131
11000000 10101000 00000001 10000011
8 bits = 1 byte = 1 octet
---
32 bits = 4 bytes

Since one byte is 8 bits, the maximum decimal value for each byte is 255.

## DHCP

DHCP stands for Dynamic Host Configuration Protocol.

### Later days
IPv4 address configuration used to be a manual process.
* IP address;
* Subnet mask;
* Gateway;
* DNS servers;
* NTP servers; and
* etc.

### Nowadays
DHCP provides automatic address and IP configuration for almost all devices.

## APIPA

APIPA stands for Automatic Private IP Addressing

A link-local address.
* Can only communicate to other local devices.
* No forwarding by routers.
* Automatically assigned.

### Reserved Addresses
IETF has reserved 169.254.0.1 through 169.254.255.254.
* First and last 256 addresses are reserved.
* Functional block of 169.254.1.0 through 169.254.254.255.

> [!NOTE]
> Uses ARP to confirm the address isn't currently in use.

## IPv4 address problem

* There are far more devices than IPv4 addresses.
* The use and registration of IP address ranges is problematic.
    * Unused and non-continuous address blocks
    * Complete depletion of available addresses.

## Private IP address ranges
* More public IP addresses.
* Huge private IP address ranges.
    * Properly design and scale large networks.
* Private IP addresses are not Internet-routable.
    * But can be routed internally.
    * Use Network Address Translating (NAT) for everything else.

> [!TIP]
> Defined in RFC 1918

### Public addresses vs. private addresses
#### RFC 1918 private IP addresses
|IP address range|Number of addresses|Classful description|Largest CIDR block (subnet mask)|Host ID size|
|:-:|:-:|:-:|:-:|:-:|
|10.0.0.0 - 10.255.255.255|16.777.216|single class A|10.0.0.0/8 (255.0.0.0)|24 bits|
|172.16.0.0 - 172.31.255.255|1.048.576|16 contiguous class Bs|172.16.0.0/12 (255.240.0.0)|20 bits|
|192.168.0.0 - 192.168.255.255|65.536|256 contiguous class Cs|192.168.0.0/16 (255.255.0.0)|16 bits|

## Classful subnetting

Very specific subnetting architecture. But still referenced in casual conversation.

> [!ATTENTION]
> Not used since 1993.

Used as a starting point when subnetting.

### Subnet classes
|Class|Leading Bits|Network Bits|Remaining Bits|Number of Networks|Host per Network|Default Subnet Mask|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Class A|0xxx (0-127)|8|24|128|16.777.214|255.0.0.0|
|Class B|10xx (128-191)|16|16|16.384|65.534|255.255.0.0|
|Class C|110x (192-223)|24|8|2.097.152|254|255.255.255.0|
|Class D *Multicast*|1110 (224-239)|Not defined|Not defined|Not defined|Not defined|Not defined|
|Class E *Reserved*|1111 (240-255)|Not defined|Not defined|Not defined|Not defined|Not defined|

## Construction of a subnet

### Network address
* First IP address of a subnet
* Set all hosts bits to 0 (0 decimal)

Example: *192.168.0.0*

### First usable host address
* One number higher than the network address

Example: *192.168.0.1*

### Network broadcast address
* The last IP address of a subnet
* Set all host bits to 1 (255 decimal)

Example: *192.168.255.255*

### Last usable host address
* One number lower than the broadcast address

Example: *192.168.255.254*

### Examples

IP address: 10.74.222.11
* Class: *A*
* Subnet mask: *255.0.0.0*

|Description|Network|Host|
|:-|:-:|:-:|
|**IP Address**|10.|74.222.11|
|**Network Address** (Set all host bits to 0)|10.|0.0.0|
|**First host address** (Add one)|10.|0.0.1|
|**Broadcast address** (Set all host bits to 1)|10.|255.255.255|
|**Last host address** (Subtract one)|10.|255.255.254|

IP address: 172.16.88.200
* Class: *B*
* Subnet mask: *255.255.0.0*

|Description|Network|Host|
|:-|:-:|:-:|
|**IP Address**|172.16.|88.200|
|**Network Address** (Set all host bits to 0)|172.16.|0.0|
|**First host address** (Add one)|172.16.|0.1|
|**Broadcast address** (Set all host bits to 1)|172.16.|255.255|
|**Last host address** (Subtract one)|172.16.|255.254|

IP address: 192.168.4.77
* Class: *C*
* Subnet mask: *255.255.255.0*

|Description|Network|Host|
|:-|:-:|:-:|
|**IP Address**|192.168.4.|77|
|**Network Address** (Set all host bits to 0)|192.168.4.|0|
|**First host address** (Add one)|192.168.4.|1|
|**Broadcast address** (Set all host bits to 1)|192.168.4.|255|
|**Last host address** (Subtract one)|192.168.4.|254|

## Classless subnetting

Classless Inter-Domain Routing
* Created around 1993
* Removed the restrictions created by classful subnet masks
* Has a "Cider" block notation

Subnet masks can be expressed as decimal or in CIDR notation

```
[IP Address]/[Number of Subnet Bits] = 192.168.1.44/24
```

|Binary|Decimal|CIDR|
|:-:|:-:|:-:|
|11111111.00000000.00000000.00000000|255.0.0.0|/8|
|11111111.11111111.00000000.00000000|255.255.0.0|/16|
|11111111.11111111.11111111.00000000|255.255.255.0|/24|

## Calculating IPv4 Subnets and Hosts

### Variable Length Subnet Masks - VLSM

Class-based networks are inefficient and the subnet mask is based on the network class.

* **VLSM** allow network administrator to define their own masks. Allows customizing the subnet mask to specific network requirements.
* Use different subnet masks in the same classful network.
    * 10.0.0.0/8 is the class A network.
    * 10.0.1.0/24 and 10.0.8.0/26 would be **VLSM**.

### Defining subnets

Network: `192.168.1.0/24`
We need an IP addressing scheme with more than one network address that can support 40 devices per subnet.

|Subnet Mask in Decimal|Subnet Mask in Binary|CIDR Notation|Networks|Hosts per Network|
|:-:|:-:|:-:|:-:|:-:|
|`255.255.255.0`|`11111111.11111111.11111111.00000000`|`/24`|1|254|
|`255.255.255.128`|`11111111.11111111.11111111.10000000`|`/25`|2|126|
|`255.255.255.192`|`11111111.11111111.11111111.11000000`|`/26`|4|62|
|`255.255.255.224`|`11111111.11111111.11111111.11100000`|`/27`|8|30|
|`255.255.255.240`|`11111111.11111111.11111111.11110000`|`/28`|16|14|
|`255.255.255.248`|`11111111.11111111.11111111.11111000`|`/29`|32|6|
|`255.255.255.252`|`11111111.11111111.11111111.11111100`|`/30`|64|2|
|`255.255.255.254`|`11111111.11111111.11111111.11111110`|`/31`|128|1|

Although we can conclude that a `/26` subnet can hold 40 devices. We can speed up the process:

$$
\begin{align*}
192.168.1.0 = & 11000000.10101000.00000001.00000000 \\
255.255.255.192 = & 
    \begin{align*} 
    & \color{blue} 11111111.11111111.11111111.   & \color{orange}11                & \color{green}000000 \\
    & \colorbox{blue}{Network=24 \text{bits}}    & \colorbox{orange}{Subnet=2}     & \colorbox{green}{Host=6} 
    \end{align*}

\end{align*}
\\ \text{Total Subnets}=2\ \text{bits}=2^2=\bold{4}
\\ \text{Hosts per Subnet}=6\ \text{bits}=64-2=\bold{62}
$$

Number of subnets = 
$$
2^{\text{subnet bits}}
$$

Hosts per subnet = 
$$
2^{\text{host bits}}-2
$$

### Four important addresses

* Network address / subnet ID &rarr; The first address in the subnet
* Broadcast address &rarr; The last address in the subnet
* First available host address &rarr; One more than the network address
* Last available host address &rarr; One less than the broadcast address

```
Address: 192.168.1.0
Netmask: 255.255.255.192 = /26
Hosts/Net: 62

Network: 192.168.1.0/26
Broadcast: 192.168.1.63
First Host: 192.168.1.1
Last Host: 192.168.1.62

Network: 192.168.1.64/26
Broadcast: 192.168.1.127
First Host: 192.168.1.65
Last Host: 192.168.1.126

Network: 192.168.1.128/26
Broadcast: 192.168.1.191
First Host: 192.168.1.129
Last Host: 192.168.1.90

Network: 192.168.1.192/26
Broadcast: 192.168.1.255
First Host: 192.168.1.193
Last Host: 192.168.1.254
```

### Finding the broadcast address

1. IP Address: `165.245.77.14`

    Subnet mask: `255.255.240.0`

    Subnet ID: `165.245.64.0`

2. Subtract the interesting octet mask from 256
   
   $$256-240=16$$
   
   > The magic number is **16**

3. Calculate Subnet ID + Magic Number - 1

    $$64+16-1=79$$

#### Helpful chart

**CIDR to decimal charts**





<table>
  <tr>
    <th>CIDR for interesting octet 2</th>
    <td>/9</td>
    <td>/10</td>
    <td>/11</td>
    <td>/12</td>
    <td>/13</td>
    <td>/14</td>
    <td>/15</td>
    <td>/16</td>
  </tr>
  <tr>
    <th>CIDR for interesting octet 3</th>
    <td>/17</td>
    <td>/18</td>
    <td>/19</td>
    <td>/20</td>
    <td>/21</td>
    <td>/22</td>
    <td>/23</td>
    <td>/24</td>
  </tr>
  <tr>
    <th>CIDR for interesting octet 4</th>
    <td>/25</td>
    <td>/26</td>
    <td>/27</td>
    <td>/28</td>
    <td>/29</td>
    <td>/30</td>
    <td style="background:lightgray; opacity: 0.2;"></td>
    <td style="background:lightgray; opacity: 0.2;"></td>
  </tr>
  <tr>
    <th>Magic number</th>
    <td>128</td>
    <td>64</td>
    <td>32</td>
    <td>16</td>
    <td>8</td>
    <td>4</td>
    <td>2</td>
    <td>1</td>
  </tr>
  <tr>
    <th>Subnet mask for interesting octet</th>
    <td>128</td>
    <td>192</td>
    <td>224</td>
    <td>240</td>
    <td>248</td>
    <td>252</td>
    <td>254</td>
    <td>255</td>
  </tr>
</table>

<div style="display: flex; gap: 20px;">
    <div style="flex: 1;">
        <table>
            <tr>
                <th colspan=3>CIDR</th>
                <th>Decimal</th>
            </tr>
            <tr> 
                <td>/9</td>
                <td>/17</td>
                <td>/25</td>
                <td style="text-align:center;">128</td>
            </tr>
            <tr> 
                <td>/10</td>
                <td>/18</td>
                <td>/26</td>
                <td style="text-align:center;">192</td>
            </tr>
            <tr> 
                <td>/11</td>
                <td>/19</td>
                <td>/27</td>
                <td style="text-align:center;">224</td>
            </tr>
            <tr> 
                <td>/12</td>
                <td>/20</td>
                <td>/28</td>
                <td style="text-align:center;">240</td>
            </tr>
            <tr> 
                <td>/13</td>
                <td>/21</td>
                <td>/29</td>
                <td style="text-align:center;">248</td>
            </tr>
            <tr> 
                <td>/14</td>
                <td>/22</td>
                <td>/30</td>
                <td style="text-align:center;">252</td>
            </tr>
            <tr> 
                <td>/15</td>
                <td>/23</td>
                <td>/31</td>
                <td style="text-align:center;">254</td>
            </tr>
            <tr> 
                <td>/16</td>
                <td>/24</td>
                <td>/32</td>
                <td style="text-align:center;">255</td>
            </tr>
        </table>
    </div>
    <div style="flex: 1;">
        <table>
            <tr>
                <th>CIDR</th>
                <th>Decimal</th>
            </tr>
            <tr>
                <td>/9</td>
                <td style="text-align: center;">255.128.0.0</td>
            </tr>
            <tr>
                <td>/10</td>
                <td style="text-align: center;">255.192.0.0</td>
            </tr>
            <tr>
                <td>/11</td>
                <td style="text-align: center;">255.224.0.0</td>
            </tr>
            <tr>
                <td>/12</td>
                <td style="text-align: center;">255.240.0.0</td>
            </tr>
            <tr>
                <td>/13</td>
                <td style="text-align: center;">255.248.0.0</td>
            </tr>
            <tr>
                <td>/14</td>
                <td style="text-align: center;">255.252.0.0</td>
            </tr>
            <tr>
                <td>/15</td>
                <td style="text-align: center;">255.254.0.0</td>
            </tr>
            <tr>
                <td>/16</td>
                <td style="text-align: center;">255.255.0.0</td>
            </tr>
            <tr>
                <td>/17</td>
                <td style="text-align: center;">255.255.128.0</td>
            </tr>
            <tr>
                <td style="text-align: center;">...</td>
                <td style="text-align: center;">...</td>
            </tr>
        </table>
    </div>
</div>
