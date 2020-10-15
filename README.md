# Network Automation

### Aim of the project

### Setup

### Required network to be created

```
(Internet) ---> HAProxy
				(internal network using private address range; 10.0.1.0/27)
				+--->A
				+--->B
				+--->C
(Internet) --->	Bastion
```

#### Creation of VPC in AWS


1. Create VPC with name NetworkAutomation (CIDR Block: `10.0.0.0/16`)
2. Create two subnets
	- PublicSubnet (CIDR Block: `10.0.0.0/27`)
	- PrivateSubnet (CIDR Block: `10.0.1.0/27`)

#### Security (security in AWS is stateful (which mean if inbound is defined outbound is automatically defined))

