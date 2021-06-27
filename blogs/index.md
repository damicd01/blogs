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

## CIDR important to understand

The way it works is that it defines and IP range in the following manner:

xx.xx.xx.xx/32 - equals to 1 IP

xx.xx.xx.xx/0 - equals to all IPs

What dictates the size of the subnet is the Subnet Mask - Here is a quick reference table of how many IPs each subnet will include

/32

1

/31

2

/30

4

/29

8

/28

16

/27

32

/26

64

/25

128

/24

256

/23

512

/22

1024

/21

2048

/20

4096

/19

8192

/18

16384

/17

32768

/16

65536

/0

All IPs

This is another quick reference which dictates which octet can change depending on the Subnet Mask assigned

/32

No Octet can Change - xx.xx.xx.xx

/24

Last Octet - xx.xx.xx.xx

/16

Last 2 Octets - xx.xx.xx.xx

/8

Last 3 Octets - xx.xx.xx.xx

/0

All 4 Octets - xx.xx.xx.xx

There is a also the concept of Private IPs and Public IPs which is worth covering.  The private IPs are as follows:

10.x.x.x.x - Usually big networks

172.x.x.x - AWS default CIDR

192.x.x.x - Usually found in home networks

 

Default VPC Walkthrough
Before we dive into the specifics of how we create our own VPC lets have a look at the default VPC which comes with every newly created AWS account

By default all new instances we create get launched in the default VPC unless we specifically define a new one alongside a subnet within it

As we have seen so far all instances that we have launched get the following:

Internet connectivity

Public and Private IP

Public and Private DNS name

A VPC out of the box gets the following in order to make it operational

VPC 

Subnets - one per AZ

Route Table - one which all subnets map to

Internet Gateway - one created at VPC level which all subnets use

Network ACLs - one which all subnets use

A VPC essentially acts as a big container for all the subnets which get created within it, when you think of subnets think of partitions of the whole VPC which are tied to AZs within the region

Here how the Default VPC looks - as you can see the VPC is a /16 which is the largest CIDR can be allocated within AWS

