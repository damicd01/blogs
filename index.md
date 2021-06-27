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

When a new account is opened with AWS you will get a default VPC with Subnets already predefined.  Within these Subnets you are able to spin up EC2 instances and be able to access the internet from within them as well as being able to access the instances from the internet providing the Security Groups assigned to the instances allow inbound access.  

#### This is an example default VPC
![Alt text](defaultvpc.png?raw=true)

#### These are the Subnets defined within the VPC
![Alt text](defaultsubnets.png?raw=true)

As you can see the Subnets are /20 and they allow 4091 IPs, AWS will always reserve 5 addresses within a subnet so instead of getting 4096 as per the calculations above you get 4091.  Below is a table which shows how many IPs each Subnet Mask can have

| Subnet Mask | Number of IPs |
|-------------|---------------|
|    /32      |       1       |
|    /31	  |       2       |
|    /30	  |       4       |
|    /29	  |       8       |
|    /28	  |       16      |
|    /27	  |       32      |
|    /26	  |       64      |
|    /25	  |       128     |
|    /24	  |       256     |
|    /23	  |       512     |
|    /22	  |       1024    |
|    /21	  |       2048    |
|    /20	  |       4096    |
|    /19	  |       8192    |
|    /18	  |       16384   |
|    /17	  |       32768   |
|    /16	  |       65536   |
|    /0	      |       All IPs |