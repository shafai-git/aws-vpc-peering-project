# AWS VPC Peering — Resource Inventory

**Author:** Shafai Ahmed Rizvi  
**AWS Region:** Europe (Stockholm) — `eu-north-1`

## 1. VPCs

| Resource | Name | CIDR |
|---|---|---|
| VPC A | ewb-vpc-a | 10.10.0.0/16 |
| VPC B | ewb-vpc-b | 10.20.0.0/16 |

## 2. Subnets

| VPC | Subnet | CIDR | Purpose |
|---|---|---|---|
| VPC A | ewb-a-public | 10.10.1.0/24 | Public subnet and bastion host |
| VPC A | ewb-a-private | 10.10.2.0/24 | Private application instance |
| VPC B | ewb-b-private | 10.20.1.0/24 | Private application instance |

## 3. VPC Peering

| Resource | Value |
|---|---|
| Peering connection | ewb-a-b-peer |
| Peering ID | pcx-0370124e0cefd7ad8 |
| Status | Active |
| Connected networks | 10.10.0.0/16 ↔ 10.20.0.0/16 |

## 4. EC2 Instances

| Instance | Private IP | Role |
|---|---|---|
| ewb-bastion | 10.10.1.10 | Bastion host |
| ewb-app-a | 10.10.2.10 | Private application instance in VPC A |
| ewb-app-b | 10.20.1.10 | Private application instance in VPC B |

## 5. Routing

- VPC A public route table: local route, route to VPC B through peering, and default route through the Internet Gateway.
- VPC A private route table: local route and route to VPC B through peering.
- VPC B private route table: local route and route to VPC A through peering.

## 6. Connectivity Verification

- Bastion-to-App-A ping: successful.
- Bastion-to-App-B ping: successful.
- App-A-to-App-B ping: successful after the ICMP security rule was restored.
- App-B-to-App-A ping: successful.
- SSH access to App-B through the bastion: successful.
- Controlled failure test: removing the relevant inbound ICMP rule caused ping to fail; restoring the rule restored connectivity.

## 7. Security Notes

- SSH access is restricted using security-group rules.
- Application instances use private IP addresses.
- No private SSH keys, passwords, or access tokens should be committed to this repository.

## 8. Cleanup Status

AWS resource cleanup has not yet been verified. Update this section only after checking the actual resource status in the AWS console.
