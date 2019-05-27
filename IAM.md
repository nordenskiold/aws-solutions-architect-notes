## Identity Access Management

### Overview
AWS Identity and Access Management (IAM) enables you to manage access to AWS services and resources securely. Using IAM, you can create and manage AWS users and groups, and use permissions to allow and deny their access to AWS resources. 
    
#### Features
- Centralised control of your AWS account
- Shared Access to your AWS account
- Granular Permissions
- Identity Federation (including Active Directory, Facebook, Linkedin, etc)
- Multifactor Authentication
- Provides temporary access for users/devices/services where necessary
- Allows you to set up your own password rotation policy
- Integrates with many different AWS services
- Supports PCI DSS Compliance

#### Terminology
**Users**<br>
End Users such as people, employees of an organization, etc.

**Groups**<br>
A collection of users. Each user in the group will inherit the permissions of the group

**Policies**<br>
Policies are made up of documents called Policy documents. These documents are in a format called JSON and they give permissions as to what a User/Group/Role is able to do.

**Roles**<br>
You create roles and then assign them to AWS Resources.

### Key Take Aways
- **IAM is universal**. It does not apply to individual regions.
- The **"root account"** is simply the account created when first setup your AWS account. It has complete Admin access.
- New Users have **NO permissions** when first created
- New Users are assigned **Access Key ID & Secret Access Keys** when first created.
- **Access Key ID & Secret Access Keys** are used to access AWS via APIs and the Amazon Command Line Interface (CLI).
- **Access Key ID & Secret Access Keys** are only viewable once during the new user creation. If lost, the keys must be regenerated through IAM.
- Always setup Multifactor Authentication on your root account
- You can create and customize your own password rotation policies

- Roles are more secure than storing your access key and secret access key on individual EC2 instances
- Roles are easier to manage
- Roles can be assigned to an EC2 instance after it is created using both the AWS console and the AWS CLI
