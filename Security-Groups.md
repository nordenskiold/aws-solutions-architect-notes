## Security Groups

### Overview
AWS security groups (SGs) are associated with EC2 instances and provide security at the protocol and port access level. Each security group –  working much the same way as a firewall – contains a set of rules that filter traffic coming into and out of an EC2 instance. There are no ‘Deny’ rules. Rather, if there is no rule that explicitly permits a particular data packet, it will be dropped.


### Key Take Aways
- All inbound traffic is blocked by default
- All Outbound traffic is allowed
- Changes to Security Groups take effect immediately
- You can have nay number of EC2 instances within a security group
- You can have multiple security groups attached to EC2 instances
- Security Groups are **STATEFUL**
- If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again
- You cannot block specific Ip addressed using Security Groups, instead use Network Access Control Lists
- You can specify allow rules, but not deny rules