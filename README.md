
**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** Albert  
**Email:** tapcyberx@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC Virtual Private Cloud (VPC) is like managing your own city inside that country. You can design neighborhoods (i.e. subnets, which you'll learn about in a second), traffic rules, and security measures to control how the different resources, like EC2 instances and S3 buckets, are connected and work together inside your VPC.

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to build a secure and isolated network environment for launching AWS resources. I configured subnets, route tables, security group, deploy network ACLs  and attached an internet gateway to allow controlled access to the internet.

### One thing I didn't expect in this project was...

As always the secret mission is a game changer in how your use CloudShell (CLI Command).

### This project took me...

Approximately 4h more or less.

---

## Route tables

Route tables are like the GPS that directs traffic within my VPC to the correct destination.

Routes tables are needed to make a subnet public because a subnet needs to have a route to an internet gateway in order to be considered public. A route table is the only way to establish this connection.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean the destination is the range of IP addresses that traffic in my VPC is trying to reach. The target is the road/path that the traffic will use to get to their destination.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of my Nextwork IG (internet gateway).

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are like chekpoint that monitor both inbound and outbound traffic at the resource level.

 

### Inbound vs Outbound rules

Inbound rules are the rules that monitor or restrict inbound traffic. I configured an inbound rule that allow all user visiting e.g. a web app through http traffic in port 80.


Outbound rules are the monitor or restrict outbound traffic By default, my security group's outbound rule will allow all outbound traffic.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are like a traffic cops stationed at every entry and exit point of your subnet, checking each data packet against a table of ACL rules before allowing them through.

### Security groups vs. network ACLs

Security groups act at the instance (resource) level they control inbound and outbound traffic for each individual resource (like an EC2 instance). Every resource in a VPC is associated with one or more security groups.

Network ACLs (Access Control Lists) operate at the subnet level they control traffic in and out of entire subnets, applying rules to all resources within that subnet.

In short, security groups are stateful (responses are automatically allowed), while network ACLs are stateless (rules must be explicitly defined for both directions).

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all incoming / outgoing traffic.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all the incoming outgoing traffic.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC Instead of my usual region, I used us-west-1 Teams would use multiple regions to improve latency for their end users and protect themselves from natural disasters and other risks - if one Region experiences an outage, other Regions can maintain operations.

EC2 Global View is a tool where you can find and manage your EC2 and VPC resources across all AWS Regions from a single dashboard. EC2 instances need VPCs to send and receive any data, which is why the EC2 Global View is showing us networking resources like security groups and VPCs too.

Now that I've learnt about EC2 Global View, I'd use it again for multi-region deployments.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-networks-security_b03ea6162)

---

---
