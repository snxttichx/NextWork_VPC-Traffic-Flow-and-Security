<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** NATTICHA SUKHAWAT  
**Email:** 6631502015@lamduan.mfu.ac.th

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create a private and isolated network inside AWS. It is useful because it allows you to securely organize cloud resources, control network traffic, manage IP addresses and subnets, and connect resources to the internet in a controlled way.


### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to create and manage a private cloud network in AWS. I configured a VPC, public subnet, route table, security group, and Network ACL, then connected the VPC to the internet using an Internet Gateway. I also used AWS CLI and EC2 Global View to manage and track resources across different AWS regions.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was how many networking components need to work together just to allow internet access. I learned that creating a VPC alone is not enough — route tables, security groups, Network ACLs, and an Internet Gateway all play important roles in controlling traffic and security.

### This project took me...

It took me about 1–2 hours to complete this project, including configuring VPC networking components, setting up security rules, using AWS CLI in AWS CloudShell, and exploring EC2 Global View across multiple AWS regions.

---

## Route tables

A route table is a set of rules that controls where network traffic goes inside a VPC. It works like a GPS for the subnet by directing traffic to the correct destination, such as other resources inside the VPC or the internet through an Internet Gateway. When a route table includes a route to an Internet Gateway and is associated with a subnet, that subnet becomes a public subnet.

A route table is needed to make a subnet public because it provides a route that sends internet traffic (`0.0.0.0/0`) to an Internet Gateway. Without this route, resources in the subnet cannot communicate with the internet, so the subnet remains private.


![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

A route’s destination is the IP address range that the traffic wants to reach, while the target is the path or resource that the traffic uses to get there, such as a local network or an Internet Gateway.

The route in my route table that directed internet-bound traffic to my Internet Gateway had a destination of `0.0.0.0/0` and a target of the Internet Gateway (`igw-0657fa80e4a2fb9c3`).


![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are virtual firewalls that control inbound and outbound traffic for AWS resources, such as EC2 instances. They use rules based on IP addresses, protocols, and port numbers to allow or block network traffic and help improve security inside a VPC.

### Inbound vs Outbound rules

An inbound rule controls what traffic is allowed to enter a resource associated with a security group. In my security group, the inbound rule allowed HTTP traffic on port 80 from `0.0.0.0/0`, which means anyone on the internet can access the resource through a web browser.

An outbound rule controls what traffic a resource is allowed to send out to other networks or the internet. My security group used the default outbound rule, which allowed all outbound traffic to any destination.

![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs (Network Access Control Lists) are security layers that control inbound and outbound traffic at the subnet level in a VPC. They use rules to allow or deny specific traffic based on IP addresses, protocols, and ports before the traffic can enter or leave the subnet.

### Security groups vs. network ACLs

Security groups and Network ACLs both help protect resources in a VPC, but they work at different levels. Security groups work at the resource level, such as EC2 instances, and control traffic using allow rules only. Network ACLs work at the subnet level and can both allow and deny traffic using numbered rules. Security groups are more specific, while Network ACLs provide broader subnet-level security.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

The default rule for all default Network ACLs is to allow all inbound and outbound traffic. This means traffic can freely enter and leave the subnet unless the rules are customized.

A custom Network ACL’s inbound and outbound rules can either allow or deny specific traffic based on IP addresses, protocols, and port numbers. Unlike default ACLs, custom ACLs block all traffic by default until rules are added.

![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC resources, including a VPC, an Internet Gateway, and a Security Group. Instead of my usual region, I used a different AWS region to practice deploying resources globally. Teams would use multiple regions to improve performance for users in different locations and increase reliability if one region experiences issues.


EC2 Global View is a tool where you can find and manage EC2 and VPC resources across multiple AWS regions from one dashboard. I could even narrow down my search by region and resource type to quickly locate specific resources. Without EC2 Global View, you'd have to switch between regions manually to check and manage resources one by one.

I would use EC2 Global View again when managing AWS resources across multiple regions because it makes it easier to monitor and track resources from one place. It is especially useful for large projects or global applications that use resources in different AWS regions.

![Image](http://learn.nextwork.org/appreciative_gray_fierce_tapir/uploads/aws-networks-security_b03ea6162)

---

---
