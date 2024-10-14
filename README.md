# Project-Wordpress-Site
## Project Summary
The aim of this project is to create a high performing and highly available website for a small to medium-sized digital marketing agency called DigitalBoost. I will provide a scalable, secure, and cost effective solution that can handle traffic and seamlessly integrate with their existing infrastructure.  AWS service that would be used to achieve this are; EC2 instance, RDS, EFS, VPC, NAT Gateway, Application Load Balancer, Auto Scaling Group.
## Solution Architecture
## Project Implementation
1. Virtual Private Cloud (VPC): Amazon VPC is a logically isolated section of the Amazon Web Service(AWS) cloud where you can launch AWS resources in a virtual network that you define. VPCs are region wide. You can have up to 5 VPCs per region. Components of a VPC are;
1.Subnet: this is a segment of a VPC's IP address range where you can place groups of isolated resources. A subnet maps to an Availability Zone(AZ) i.e 1:1. You can 
   have a public and private subnet.
2. Internet Gateway: this allows resources in a VPC connect to the internet. This is attached to a VPC. You can only attach one Internet Gateway to a custom VPC.
3. Network Access Translation(NAT) Gateway: this allows resources in a privae subnet access the internet. It is created in a public subnet
4. Router: this performs routing between AZs in a region. It connects different AZs together and connects the VPC to the internet gateway. Each subnet has a route 
   table that router uses to forward traffic within the VPC.
2. Elastic Compute Cloud(EC2): this provides resizable compute capacity in the cloud that allows you to launch virtual server. Each virtual server is called an instance.
3. Elastic File System(EFS): it is a fully managed service for hosting Network File System in the cloud. It provides elastic storage capacity and you pay for what you use. It grows and shrinks as you add and remove data. You can concurrently connect up to thousands of EC2 instances from multiple AZs. It is compatible with linux based Amazon Machine Image. It uses NFSv4.1 protocol. It uses POSIX file system that has a standard file API.
4. Relational Database Service(RDS): it is a managed service that you can use to launch and manage relational databases on AWS. It is an Online Transaction Processing(OLTP) type of database. It is best suited to structured, relational data store requirements. It supports the following database engines: MySQL, PostgreSQL, Amazon Aurora, MariaDB, Microsoft SQL server, Oracle.
5. Elastic Load Balancer(ELB): this automatically distributes incoming application traffic across multiple targets such as EC2 instances, containers, IP address. It checks if the targets are healthy or not and sends traffic to only healthy targets. There are four types of ELB: Classic Load balancer - this is the oldest and provides basic load balancing at both layer 4 and layer 7, Application Load balancer - layer 7 load balacer that routes connections based on the content of the request. It supports HTTP and HTTPS protocols, Network Load Balancer - layer 4 load balancer. It allows you to deal with TCP and UDP traffic. It is high performance and can handle millions of request per seconds, Gateway Load Balancer - it operates at layer 3, you can use it to deploy, scale and manage a fleet of third party network virtual appliances in AWS. You can use it when you want your traffic to go through firewalls, intrusion detection and prevention systems, deep packet inspection systems, payload manipulation.
7. Auto Scaling Group(ASG): it is used to scale out (add EC2 instances) to match an increased load, scale in(remove EC2 instances) to match a decreased load. It ensures we have a minimum and a maximum number of EC2 instances running. It automatically launches new instances to a load balance. ASG  is free, you only pay for resources such as EC2 launched. You set a minimum capacity which is how many instances you wnat at minimum in your ASG. You set a desired capacity which is how many instances you want running in your ASG. You st a maximum capacity which is how many instances you want at a maximum in your ASG. The following are good metrics to scale on: CPU utilization, Request count per Target to make sure the number of requests per EC2 instances is stable, Average Network in/out if your application is network bound.
 ### VPC Setup
 1. I created a VPC with IP address 10.0.0.0/16
   2. I created a public subnet and a private subnet with IP address 10.0.1.0/20 and 10.0.16.0/20 respectively.
   3. I used two Availability Zones with the public subnet and private subnet in different AZ for high availability and  fault tolerance.
   4. I created an internet gateway and attached it to the VPC.
   5. I created 2 route tables, one for the public subnet and the other for the private subnet.
   6. I also configured a subnet association for the route tables.
Find screenshots below:
![Screenshot 2024-10-14 142156](https://github.com/user-attachments/assets/c53e1abe-15dc-4bdb-a4f4-ae4a1cd637b7)
![Screenshot 2024-10-14 142248 - Copy - Copy](https://github.com/user-attachments/assets/551571e4-20eb-4078-a09e-5ea08a577236)
![Screenshot 2024-10-14 142248](https://github.com/user-attachments/assets/29c30083-f21d-4aaa-9dbc-0a7ed716e703)
![Screenshot 2024-10-14 143329 - Copy - Copy](https://github.com/user-attachments/assets/d012d162-59ff-43b5-ae2e-f9e28d6e28f9)
![Screenshot 2024-10-14 143329 - Copy](https://github.com/user-attachments/assets/5b310e54-969a-4801-8d1b-8ff029bae433)
![Screenshot 2024-10-14 143329](https://github.com/user-attachments/assets/095522ac-4200-4748-b6b1-d8c90b2c3e03)
![Screenshot 2024-10-14 143445](https://github.com/user-attachments/assets/c404a832-c50d-4a6d-aa47-09903c639af5)
### NAT Gateway Setup
I configured a NAT gateway to allow resources in the private subnet access the internet.
![Screenshot 2024-10-14 142156 - Copy - Copy](https://github.com/user-attachments/assets/c31df4d0-d57a-4ab2-b0cf-89a2bd46fc4e)

   
