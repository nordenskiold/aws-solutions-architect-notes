## Elastic Block Store (EBS)

### Overview
Amazon Elastic Block Store (Amazon EBS) provides persistent block storage volumes for use with Amazon EC2 instances in the AWS Cloud. Each Amazon EBS volume is automatically replicated within its Availability Zone to protect you from component failure, offering high availability and durability. 

#### EBS Storage Types
1. **General Purpose (SSD)**
General purpose SSD volume that balances price and performance for a wide variety of transactional workloads
**API Name:** gp2
**Volume Size:** 1 GiB - 16 TiB
**Max. IOPS:** 16,000
**Use Case:** Most Work Loads

2. **Provisioned IOPS (SSD)**
Highest performance SSD volume designed for mission-critical applications
**API Name:** io1
**Volume Size:** 4 GiB - 16 TiB
**Max. IOPS:** 64,000
**Use Case:** Databases

3. **Throughput Optimised Hard Disk Drive**
Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
**API Name:** st1
**Volume Size:** 500 GiB - 16 TiB
**Max. IOPS:** 500
**Use Case:** Big Data & Data Warehouses


4. **Cold Hard Disk Drive**
Lowest cost HDD volume designed for less frequently accessed workloads.
**API Name:** sc1
**Volume Size:** 500 GiB - 16 TiB
**Max. IOPS:** 250
**Use Case:** File Servers


5. **Magnetic**
Previous generation HDD

**API Name:** Standard
**Volume Size:** 1 GiB - 1 TiB
**Max. IOPS:** 40-200
**Use Case:** Workloads where data is infrequently accessed


### Key Take Aways
- Volumes exist on EBS. Think of EBS as a virtual hard disk
- Snapshots exist on S3. Think of snapshots as a photograph of the disk
- Snapshots are point in time copies of Volumes
- Snapshots are incremental - this means that only the blocks that have changed since your last snapshot are moved to S3
- If this is your first snapshot, it may take some time to create
- To create a snapshot for Amazon EBS volumes that serve as root devices, you should stop the instance before taking the snapshot
- However you can take a snapshot while the instance is running
- You can create AMI's from both Volumes and Snapshots
You can change EBS volume sizes on the fly, including changing the size and storage type
- Volumes will **always** be in the same availability zone as the EC2 instance
- To move an EC2 volume from one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use the AMI to launch the EC2 instance in a new AZ
- To move an EC2 volume from one region to another, take a snapshot of it, create an AMI from the snapshot and then copy the AMI from one region to the other. Then use the copied AMI to launch the new EC2 instance in the new region

