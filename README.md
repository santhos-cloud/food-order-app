# Secure Three-Tier AWS Architecture

This project implements a production-grade, highly available three-tier architecture on Amazon Web Services (AWS). The infrastructure is designed with strict network segmentation to isolate the presentation, application, and data layers. The result is a secure, scalable environment suitable for real-world applications.

## Architecture Overview

The system is organized into three independent tiers within a custom Virtual Private Cloud (VPC):

- **Presentation Layer:** Public-facing Application Load Balancer (ALB).
- **Application Layer:** EC2 instances in private subnets, managed through an Auto Scaling Group.
- **Data Layer:** Amazon RDS MySQL deployed in a Multi-AZ configuration for redundancy and automated failover.

Routing, subnet isolation, and security controls ensure only intended traffic flows between layers.

## Core Features

- Custom VPC configured with a non-overlapping CIDR block.
- Six subnets across two Availability Zones providing high availability.
- Public subnets that host the ALB and NAT Gateways.
- Private application subnets running EC2 instances managed by an Auto Scaling Group.
- Isolated private database subnets hosting RDS MySQL in Multi-AZ mode.
- Application Load Balancer configured with health checks and optional HTTPS termination.
- Automated EC2 provisioning using Launch Templates and User Data.
- RDS encryption, automated backups, Multi-AZ failover, and complete private isolation.
- Security Groups and NACLs enforcing strict tier-based network access.
- IAM instance roles used to securely provide permissions without embedding credentials.

## Security Architecture

A layered security model is implemented to control access across the system:

- The database layer allows inbound traffic only from the application layer.
- The application layer accepts traffic exclusively from the load balancer.
- No direct public access is permitted to EC2 instances or the RDS database.
- Network ACLs enforce subnet-level rules, while Security Groups filter traffic at the instance level.
- IAM roles provide temporary, least-privilege permissions for EC2 operations and service access.

## Component Breakdown

| Layer | Service | Description |
|-------|---------|-------------|
| Presentation | Application Load Balancer | Public entry point responsible for routing traffic and performing health checks. |
| Application | EC2 (Auto Scaling Group) | Private compute instances running backend logic. |
| Data | Amazon RDS MySQL (Multi-AZ) | Managed database with automated failover and backups. |
| Security | Security Groups & NACLs | Instance-level and subnet-level access control. |

## Traffic Flow

1. User traffic reaches the ALB in the public subnet.
2. The ALB forwards requests to EC2 instances running in private application subnets.
3. EC2 instances communicate with the RDS database in the private data subnets.
4. Private EC2 instances use the NAT Gateway for outbound internet access.
5. RDS Multi-AZ manages replication and failover during Availability Zone disruptions.

## Deployment Components

- VPC, subnets, route tables, and routing controls
- Internet Gateway and NAT Gateways
- ALB and target groups
- Launch Template and Auto Scaling Group
- EC2 instance initialization via User Data
- Multi-AZ RDS MySQL deployment
- Tiered Security Groups and NACLs
- IAM instance roles and policies

## Summary

This architecture aligns with AWS best practices for secure, resilient, and scalable application design. It provides complete isolation between layers, fault tolerance across Availability Zones, and automated scaling and failover capabilities suited for production workloads.

