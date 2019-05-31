## Virtual Private Cloud (VPC)

### Overview
Amazon Virtual Private Cloud (Amazon VPC) lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways. 

You can easily customize the network configuration for your Amazon VPC. For example, you can create a public-facing subnet for your web servers that has access to the Internet, and place your backend systems such as databases or application servers in a private-facing subnet with no Internet access. You can leverage multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet.

*Essentially, a VPC can be thought of as a logical datacenter in AWS*

#### What can be done with a VPC?
- Launch instances into a subnet of your choosing
- Assign custom IP address ranges in each subnet
- Configure route tables between subnets
- Create internet gateway and attach it to our VPC
- Much better security control over your AWS resources
- Instance security groups
- Subnet network access control lists (ACLS)

#### Default AWS VPC
- Default VPC is user friendly, allowing you to immediately deploy instances
- All Subnets in a default VPC have a route out to the internet
- Each EC2 instance has both a public and private IP address in the default VPC

#### VPC Peering
- Allows you to connect one VPC with another via a direct network route using private IP addresses
- Instances behave as if they were on the same private network
- You can peer VPC's with other AWS accounts as well as with other VPCs in the same account
- Peering is always in a star configuration. I.e. 1 central VPC peers with 4 others. **No transitive peering** (this means that each vpc needs to have a direct connection to the other)

#### Network Address Translation (NAT) Instances and Gateways

NAT Instances are simply single EC2 instances. NAT Gateways are scalable, highly available, and implemented with redundancy. 

**NAT Instances**<br>

- When creating a NAT instance, Disable Source/Destination Check on the Instance
- NAT instances must be in a public subnet
- There must be a route out of the private subnet to the NAT instance, in order for this to work
- The amount of traffic that NAT instances can support depends on the instance size. If you are bottlenecking, increase the instance size
- You can create high availability using Autoscaling Groups, multiple subnets in different AZs, and a script to automate failover
- Behind a Security Group

**NAT Gateways**<br>

- Redundant inside the Availability Zone, but cannot span AZs
- Preferred for enterprise
- Starts at 5Gbps and scales to 45Gbps
- No need to patch (you do need to for instances)
- Not associated with security groups 
- Automatically assigned a public ip address
- You need to update your route tables after adding
- No need to disable Source/Destination checks
- If you have resources in multiple AZs and they share one NAT gateway, in the event that the NAT gateway's AZ is down, resources in the other AZs lose internet access. To create an AZ-independent architecture, create a NAT gateway in each AZ and configure your routing to ensure that resources use the NAT gateway in the same AZ

#### Network Access Control Lists (NACL)
A network access control list (ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up network ACLs with rules similar to your security groups in order to add an additional layer of security to your VPC.

- Your VPC automatically comes with a default NACL, and by adefault it **allows** all outbound and inbound traffic
- You can create custom NACLS. By default, each custom NACL **denies** all inbound and outband traffic until you add rules
- Each subnet in your VPC must be associated with a NACL. If you don't explicitly associate a subnet with a NACL, the subnet is automatically associated with the default NACL.
- You can block IP Addresses using NACLS; you cannot do this with security groups
- You can associate a NACL with multiple subnets; however, a subnet can be associated with only one NACL at a time. When you associate a NACL with a subnet, the previous association is removed
- NACLs contain a numbered list of rules that are evaluated in order, starting with the lowest numbered rule
- NACLs are stateless; responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa.). This means you need to add rules to both inbound and outbound as opposed to e.g. Security Groups which are stateful and if you add an inbound rule it is automatically added to outbound as well.

#### VPC Flow Logs
VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC. Flow log data can be published to Amazon CloudWatch Logs and Amazon S3. After you've created a flow log, you can retrieve and view its data in the chosen destination.

*Flow logs can be created at 3 levels: the VPC level, Subnet level and Network Interface Level.*

- You cannot enable flow logs for VPCs that are peered with your VPC unless the peer VPC is in your account
- You cannot tag a flow log
- After you've created a flow log, you cannot change its configuration; for example, you can't associate a different IAM role with the flow log
- Not all IP traffic is monitored
    - Traffic generated by instances when they contact the Amazon DNS server is not logged. If you use your own DNS server, then all traffic to that DNS server is logged
    - Traffic generated by a Windows instance for Amazon  Windows license activation is not logged
    - Traffic to and from 169.254.169.254 for instance metadata is not logged
    - DHCP traffic is not logged
    - Traffic to the reserved IP addresses for the dafault VPC router is not logged
    
#### Bastion Hosts
A bastion host is a special-purpose server instance specifically designed and configured to withstand attacks. It is designed to be the primary access point from the Internet and acts as a proxy to your other EC2 instances. The server generally hosts a single application, for example a proxy server, and all other services are removed or limited to reduce the threat to the server. 

- A NAT Gateway or Instance is used to provide internet traffic to EC2 instances in a private subnets
- A Bastion is used to securely administer EC2 instances (Using SSH or RDP)
- You cannot use a NAT Gateway as a Bastion host

#### Direct Connect
AWS Direct Connect is a cloud service solution that makes it easy to establish a dedicated network connection from your premises to AWS. Using AWS Direct Connect, you can establish private connectivity between AWS and your datacenter, office, or colocation environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than Internet-based connections.

- Direct connect directly connects your data center to AWS
- Useful for high throughput workloads (ie lots of network traffic) or if you need a stable and reliable secure connection

#### VPC Endpoint
A VPC endpoint enables you to privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink without requiring an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

Endpoints are virtual devices. They are horizontally scaled, redundant, and highly available VPC components that allow communication between instances in your VPC and services without imposing availability risks or bandwidth constraints on your network traffic.

There are two types of VPC endpoints: *interface endpoints* and *gateway endpoints*. 

**Interface endpoint**<br>
An interface endpoint is an elastic network interface with a private IP address that serves as an entry point for traffic destined to a supported service. Similar to an ENI (network card) within your VPC.

**Gateway endpoint**<br>
Uses route prefixes in your route table to direct traffic meant for S3 or DynamoDB (only supported services) to the gateway endpoint (similar to how NAT gateways work). Note that currently only S3 and DynamoDB support Gateway endpoints.


### Key Take Aways
- Think of VPCs as logical datacenters in AWS
- A VPC consists of IGWs (or Virtual Private Gateways), Route Tables, Network Access Control Lists, Subnets, and Security Groups
- 1 Subnet cannot be spread amongst several Availability Zones, but multiple subnets can exist in one Availability Zone
- Security Groups are Stateful, Network Access Control Lists are Stateless
- No transitive peering
- When you create a VPC a default Route Table, Network Access Control (NACL), and a default Security Group are also created
- When you create a VPC, subnets and internet gateway will *not* be created
- US-East-1A in your AWS account could be in a completely different AZ than US-East-1A in another AWS account. The AZ's are randomized.
- Amazon always reserves 5 IP addresses within your subnets
- You can only have 1 Internet Gateway per VPC
- Security Groups can't span VPCs
