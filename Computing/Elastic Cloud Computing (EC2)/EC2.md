## Overview
- Regional Service
- EC2 (Elastic Compute Cloud) is an **Infrastructure as a Service (IaaS)**
- Stopping & Starting an instance may change its public IP but not its private IP
- **AWS Compute Optimizer** recommends optimal AWS Compute resources for your workloads
- There is a vCPU-based On-Demand Instance soft limit per region

## What is User Data ?

- Some commands that run when the instance is launched for the first time (doesn't execute for subsequent runs)
- Used to automate **dynamic** boot tasks (that cannot be done using AMIs)
    - Installing updates
    - Installing software
    - Downloading common files from the internet
- Runs with the **root user privilege**

## Instance Classes

- **General Purpose(t2.micro)**
    - Great for a diversity of workloads such as **web servers** or **code repositories**
    - Balance between compute, memory & networking
- **Compute Optimized(C6g)**
    - Great for compute intensive tasks
        - Batch Processing
        - Media Transcoding
        - HPC
        - Gaming Servers
- **Memory Optimized(R6g)**
    - Great for **in-memory databases** or **distributed web caches**
- **Storage Optimized(I3)**
    - Great for storage intensive tasks (accessing local databases)
        - OLTP systems
        - Distributed File System (DFS)

## Security Groups

- **Only contain Allow rules**
- External firewall for EC2 instances (if a request is blocked by SG, instance will never know)
- Security groups rules can reference a resource by IP or Security Group

- Default SG
    - inbound traffic from the same SG is allowed
    - all outbound traffic is allowed
    
- New SG
    - all inbound traffic is blocked
    - all outbound traffic is allowed
- A security group can be attached to multiple instances and vice versa
- Bound to a VPC (and hence to a region)
- Recommended to maintain a separate security group for SSH access
- Blocked requests will give a **Time Out** error

## IAM Roles for EC2 instances

- Never enter AWS credentials into the EC2 instance, instead attach IAM Roles to the instances

## Purchasing Options

### **On-demand Instances**

- Pay per use (no upfront payment)
- Highest cost
- No long-term commitment
- Recommended for short-term, uninterrupted and **unpredictable** workloads

### **Standard Reserved Instances**

- Reservation Period: 1 year or 3 years
- Recommended for steady-state applications (like database)
- **Sell unused instances** on the Reserved Instance Marketplace

A Reserved Instance in AWS gives you a discount on your cloud costs if you commit to using a specific type of instance for a certain period (1 or 3 years). When it comes to scope, there are two options:

1. **Regional Reserved Instance**: This applies to an entire AWS region (like "Asia Pacific (Sydney)" or "US East (N. Virginia)"). It means that your discount will work on any availability zone (AZ) within that region, giving you more flexibility in where you can launch your instances.
2. **Zonal Reserved Instance**: This is tied to a specific availability zone (like "us-east-1a" or "ap-southeast-2b"). By choosing this, you're also reserving capacity in that exact zone. This is useful if you need to make sure you always have resources available in a specific zone, but it's less flexible because the discount only applies to that zone.

So, **regional** is more flexible, while **zonal** ensures guaranteed capacity in a specific part of the region.
