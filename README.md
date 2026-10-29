# AWS VPC Peering Project

**Author:** Shafai Ahmed Rizvi
**AWS Region:** Europe (Stockholm) - eu-north-1

## Overview
This project demonstrates connectivity between two Amazon VPCs using VPC Peering, private subnet routing, security groups, and a bastion host.

## Network Design
- VPC A: 10.10.0.0/16
- VPC B: 10.20.0.0/16
- Public subnet A: 10.10.1.0/24
- Private subnet A: 10.10.2.0/24
- Private subnet B: 10.20.1.0/24

## Key Components
- VPC Peering connection
- Public and private route tables
- Internet Gateway
- Bastion host for private SSH access
- Security groups controlling SSH and ICMP traffic

## Testing
The evidence includes successful pings between private instances and SSH access to App-B through the bastion. The PDF report contains the route tables, security rules, and test screenshots.

## Security
No private SSH keys, passwords, or access tokens are included.
