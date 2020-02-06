---
layout: post
title:  "Algorithms: Dynamic Programming"
categories: algorithms dynamic-programming
---

# AWS Notes
Some of these notes come from [this](https://youtu.be/jZAvKgqlrjY) wonderful presentation from AWS re:Invent

Generally speaking, no matter what you're doing in AWS there are two
foundational concepts that are important to understand:

**VPC**, or **V**irtual **P**rivate **C**loud
**IAM** or Identity and Access Management

## VPC
A virtual network, totally private and under your control, running in Amazon's
cloud.

It's where you run all of your resources (**Q** Do I HAVE to use a VPC? Is it
automatic? **A** you're given a "default" VPC)

### VPC Concepts
VPC is specific to a region, and regions have different availability zones.

### Creating an Internet-connected VPC: Steps
 - Choosing an address range
 - Creating Subnets in Availability Zones
 - Creating a Route to the internet (how we actually send traffic)
 - Authorizing traffic to/from the VPC

#### Choosing an IP address range
CIDR notation review
Classless interdomain routing. A range ofr IP Addresses

CIDR range example:
172.31.0.0/**16**
translates to
**1010 1100 0001 1111** 0000 0000 0000 0000

The `/16` means hold the top 16 bits of that translated number, but you can
vary the bottom 16 bits

#### Creating Subnets in Availability Zones
A VPC exists at the regional level, so it's possible to assign subnets to
separate availability zones.  This is a good thing because availability zones
have completely separate failure and performance characteristics and are
geographically distinct as well.  Routing traffic to specific availability
zones can make your services more secure and more performant.

You create subnets for availability zones and when you create a resource you
provide the subnet to that the resource for the availability zone that you
want to use. E.g. you could create an RDS database and a subnet for eu-west-1b
and provide that subnet as the ip for the RDS database.  It will then run in
that availability zone.

#### Routing in your VPC
 - Route tables contain rules for which packets go where
 - Your VPC has a default route table
 - But, you can assign different route tables to different subnets

(get an example of route table)

Target: local, they're basically saying if the traffic is going somewhere
inside the VPC route it local (keep it inside the VPC) if it's destined for
anywhere else drop it, we have no rules.  
But what if we want to go outside of the VPC? Like, to the internet?
That's when we need to create an internet gateway
Create one, and then when you want to send traffic to the internet, you send
it to the internet gateway.

**note** 0.0.0.0/0 (IPv4) and ::/0 are complete wildcards. 
**Q**: is the route table order dependent?

#### Authorizing Traffic to/from the VPC
AWS uses (https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)[Security Groups] to control which traffic you will accept.  This
takes the place of the more traditional FireWall that you would have to manage
in your on-prem data center.

Security Groups follow application structure

Security groups give you a dynamic way to follow the principle of least
privilege: In information security, computer science, and other fields, the principle of least privilege (PoLP), also known as the principle of minimal privilege or the principle of least authority, requires that in a particular abstraction layer of a computing environment, every module (such as a process, a user, or a program, depending on the subject) must be able to access only the information and resources that are necessary for its legitimate purpose. 
from https://en.wikipedia.org/wiki/Principle_of_least_privilege

Get some examples

### Connectivity Options for VPCs
The basics, the meat and potatoes were all included above.  Now we can discuss
how to fine tune.

One way to get internet access within a VPC -> Subnet without making it
routable to the internet is to use a NAT(Network Address Translation) gateway
**note**: this is only for IPv4, as IPv6 doesn't have a notion of private vs.
public addresses.  For IPv6 traffic you need to use an "Egress-only" Internet
gateway

**See image**

### DNS in a VPC
[https://youtu.be/jZAvKgqlrjY?t=2145](https://youtu.be/jZAvKgqlrjY?t=2145)

### AWS Services in your VPC
When you're setting up a service in your VPC, this first thing that you'll be
asked about is **security groups**.  Define which things will be accessing the
Service.

The NExt thing that needs to be taken care of is the Subnets, which is to say
"which availability zones do you want me to use?"

If you aren't using an application load balancer then you're going to be
taking a "Primary/secondary" approach.  (See diagram)

If you ARE using an application load
balancer then you can take an "active/active" approach. (See Diagram)
**Q**: How much can we do with a load balancer?  Can we do things like rout
based on geolocation?

### VPC Endpoints
Direct private connections to VPC services. As an example: accessing S3 from
a VPC.

Gateway VPC Endpoints are just entries in the route table.  They're only used
for Dynamo and S3 (I think)

S3 buckets can be configured such that they only accept traffic from
a particular VPC endpoint.

**Interface VPC Endpoints**
Backed by AWS Private Link. The way it works:
When you create the VPC endpoint it creates elastic network interfaces in the
subnets that you specify. (See Diagram)

These endpoints do NOT use a route table, they use DNS


