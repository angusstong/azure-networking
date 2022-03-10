# VNet Basics

#### [prev](./concepts.md) | [home](./welcome.md)  | [next](./connectivity.md)

## Network Planning Questions
When planning to implement virtual networks, you need to consider the following:

- Ensure non-overlapping address spaces. Make sure your VNet address space (CIDR block) does not overlap with your organization's other network ranges.
- Is any security isolation required?
- Do you need to mitigate any IP addressing limitations?
- Will there be connections between Azure VNets and on-premises networks?
- Is there any isolation required for administrative purposes?
- Are you using any Azure services that create their own VNets?

## Best practices

As you build your network in Azure, it is important to keep in mind the following universal design principles:

- Ensure non-overlapping address spaces. Make sure your VNet address space (CIDR block) does not overlap with your organization's other network ranges.
- Your subnets should not cover the entire address space of the VNet. Plan ahead and reserve some address space for the future.
- It is recommended you have fewer large VNets rather than multiple small VNets. This will prevent management overhead.
- Secure your VNet's by assigning Network Security Groups (NSGs) to the subnets beneath them.

## How does a virtual machine connect to the network?

> Configure IP address and DNS settings outside of the VMs OS. Leave the VM to use DHCP (yes, even for NVAs).

Subnets and other VNets
- Connected by default.
- A basic NSG provides minimum ingress/egress controls.

Internet locations
- NAT is performed by the networking fabric by-default.
- A public IP is **NOT** needed for internet access.

On-premises network
- Via the internet.
- Via a Gateway.

More information for [Outbound connection (flows)](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections)

## How do you connect to a virtual machine?

Azure Bastion (or even via console)
- RDP and SSH over HTTPS.
- Secure, simple, effective.
- (As of 05-Nov-20) [VNet peering and Azure Bastion (Preview)](https://docs.microsoft.com/en-us/azure/bastion/vnet-peering) is available in Preview.

Via an on-premises connection
- Connecting to the virtual machine's private IP address.

Via the internet
- Through an Application Gateway or Firewall.
- Assigning a public IP to the virtual machine directly.

## What are the basics?

![VNet Reference](/png/basics.png)
[Virtual network basics](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-faq)

