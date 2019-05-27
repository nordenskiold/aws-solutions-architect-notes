## Elastic Block Store (EBS)

### Overview
Amazon EBS encryption offers a straight-forward encryption solution for your EBS volumes that doesn't require you to build, maintain, and secure your own key management infrastructure. When you create an encrypted EBS volume and attach it to a supported instance type, the following types of data are encrypted:

- Data at rest inside the volume
- All data moving between the volume and the instance
- All snapshots created from the volume
- All volumes created from those snapshots

Encryption operations occur on the servers that host EC2 instances, ensuring the security of both data-at-rest and data-in-transit between an instance and its attached EBS storage.

You can encrypt both the boot and data volumes of an EC2 instance. Encryption is supported by all EBS volume types.

#### How To Encrypt Your EBS Volume

### Key Take Aways
- Snapshots of encrypted volumes are encrypted automatically
- Volumes restored from encrypted snapshots are encrypted automatically
- You can share snapshots, but only if they are unencrypted
- These snapshots can be shared with other AWS accounts or made public
