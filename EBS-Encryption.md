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
**Method 1 (easiest)**
When launching a new EC2 instance, when configuring "storage types", use the right-most drop-down to select encryption on your root EBS volume.

**Method 2**

- Create a Snapshot of the unencrypted root device volume
- Create a copy of the Snapshot and select the encrypt option
- Create an AMI from the encrypted Snapshot
- Use that AMI to launch new encrypted instances

### Key Take Aways
- Snapshots of encrypted volumes are encrypted automatically
- Volumes restored from encrypted snapshots are encrypted automatically
- You can share snapshots, but only if they are unencrypted
- These snapshots can be shared with other AWS accounts or made public
