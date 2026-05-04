# Designing the Cloud

## Virtual Networks

## Network Function Virtualization (NFV)
* Replace physical network devices with virtual versions
    * Manage from Hypervisor
* Same functionality as a physical device
    * Routing, switching, load balancing, firewalls, etc.
* Quickly and easily deploy network functions
* Many different deployment options
    * Virtual machine, container, fault tolerance, etc.

## Connecting to the cloud
* VPN (Virtual Private Network)
    * Site-to-site VPN through the Internet
* Virtual Private Cloud Gateway / Internet Gateway
    * Connects users on the Internet
* VPC NAT Gateway
    * NAT stands for Network Address Translation
    * Private cloud subnets connect to external resources
    * External resources cannot access the private cloud
* VPC Endpoint
    * Direct connection between cloud provider networks
