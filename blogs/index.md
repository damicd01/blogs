# AWS VPC what is it and how it works

## Overview

In this section we will cover what a VPC is in the AWS ecosystem, its use cases and how we go about configuring one.

## So what is a VPC?

VPC stands for Virtual Private Cloud and you can think of it as the "shell" or the "container" which will wrap around the Subnets defined within it.  Another way of thinking about it is to imagine the VPC as the overarching network configuration that spans across an AWS Region with the Subnets being partitions of the VPC allocated to each of the Availability Zones.

The following are the key concepts for VPCs:

1. Virtual private cloud (VPC) — A virtual network dedicated to your AWS account.
2. Subnet — A range of IP addresses in your VPC.
3. Route table — A set of rules, called routes, that are used to determine where network traffic is directed.
4. Internet gateway — A gateway that you attach to your VPC to enable communication between resources in your VPC and the internet.
5. VPC endpoint — Enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network. For more information, see AWS PrivateLink and VPC endpoints.
5. CIDR block — Classless Inter-Domain Routing. An internet protocol address allocation and route aggregation methodology. For more information, see https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing

![Alt text](defaultvpc.png?raw=true "Default VPC")

