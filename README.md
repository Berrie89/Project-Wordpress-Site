# Project-Wordpress-Site
## Project Summary
The aim of this project is to create a high performing and highly available website for a small to medium-sized digital marketing agency called DigitalBoost. I will provide a scalable, secure, and cost effective solution that can handle traffic and seamlessly integrate with their existing infrastructure.  AWS service that would be used to achieve this are; EC2 instance, RDS, EFS, VPC, NAT Gateway, Application Load Balancer, Auto Scaling Group.
## Solution Architecture
## Project Implementation
1. Virtual Private Cloud (VPC): Amazon VPC is a logically isolated section of the Amazon Web Service(AWS) cloud where you can launch AWS resources in a virtual network that you define. VPCs are region wide. You can have up to 5 VPCs per region. Components of a VPC are;
   i. Subnet: this is a segment of a VPC's IP address range where you can place groups of isolated resources. A subnet maps to an Availability Zone(AZ) i.e 1:1. You can have 
   a public and private subnet.
   ii. Internet Gateway: this allows resources in a VPC connect to the internet. This is attached to a VPC. You can only attach one Internet Gateway to a custom VPC.
   iii. Network Access Translation(NAT) Gateway: this allows resources in a privae subnet access the internet. It is created in a public subnet
   iv. Router: this performs routing between AZs in a region. It connects different AZs together and connects the VPC to the internet gateway. Each subnet has a route table 
   that router uses to forward traffic within the VPC.
2. Elastic Compute Cloud(EC2): this provides resizable compute capacity in the cloud that allows you to launch virtual server. Each virtual server is called an instance.
3. Elastic File System(EFS): it is a fully managed service for hosting Network File System in the cloud. It provides elastic storage capacity and you pay for what you use. It grows and shrinks as you add and remove data. You can concurrently connect up to thousands of EC2 instances from multiple AZs. It is used by Linux-based applications.
4. Relational Database Service(RDS): it is a managed service that you can use to launch and manage relational databases on AWS. It is an Online Transaction Processing(OLTP) type of database. It is best suited to structured, relational data store requirements. It supports the following database engines: MySQL, PostgreSQL, Amazon Aurora, MariaDB, Microsoft SQL server, Oracle.
