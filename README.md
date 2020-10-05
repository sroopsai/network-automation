# Network Automation

### Aim of the project

### Setup

#### Creation of VPC in AWS


1. Create VPC with name NetworkAutomation (CIDR Block: `10.0.0.0/16`)
2. Create two subnets
	- PublicSubnet (CIDR Block: `10.0.0.0/24`)
	- PrivateSubnet (CIDR Block: `10.0.1.0/24`)

#### Security (security in AWS is stateful (which mean if inbound is defined outbound is automatically defined))

Anywhere --> CIDRBlock(0.0.0.0/0)

1. Bastion/JumpBox (PublicSubnet)
	- Inbound: SSH (Anywhere)

2. WebServers (PrivateSubnet)
	- Inbound: SSH (PublicSubnet)
	- Inbound: HTTP, HTTPS (PrivateSubnet)

3. HAProxy (PrivateSubnet)
	- Inbound: SSH (PrivateSubnet)
	- Inbound: HTTP, HTTPS (Anywhere)