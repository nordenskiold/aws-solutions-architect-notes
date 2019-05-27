## Elastic Block Store (EBS)

### Overview
Amazon Elastic Block Store (Amazon EBS) provides persistent block storage volumes for use with Amazon EC2 instances in the AWS Cloud. Each Amazon EBS volume is automatically replicated within its Availability Zone to protect you from component failure, offering high availability and durability. 

#### EBS Storage Types
1. **General Purpose (SSD)**<br>
General purpose SSD volume that balances price and performance for a wide variety of transactional workloads<br>
**API Name:** gp2<br>
**Volume Size:** 1 GiB - 16 TiB<br>
**Max. IOPS:** 16,000<br>
**Use Case:** Most Work Loads<br>

2. **Provisioned IOPS (SSD)**<br>
Highest performance SSD volume designed for mission-critical applications<br>
**API Name:** io1<br>
**Volume Size:** 4 GiB - 16 TiB<br>
**Max. IOPS:** 64,000<br>
**Use Case:** Databases<br>

3. **Throughput Optimised Hard Disk Drive**<br>
Low cost HDD volume designed for frequently accessed, throughput-intensive workloads<br>
**API Name:** st1<br>
**Volume Size:** 500 GiB - 16 TiB<br>
**Max. IOPS:** 500<br>
**Use Case:** Big Data & Data Warehouses<br>


4. **Cold Hard Disk Drive**<br>
Lowest cost HDD volume designed for less frequently accessed workloads.<br>
**API Name:** sc1<br>
**Volume Size:** 500 GiB - 16 TiB<br>
**Max. IOPS:** 250<br>
**Use Case:** File Servers<br>


5. **Magnetic**<br>
Previous generation HDD<br>
**API Name:** Standard<br>
**Volume Size:** 1 GiB - 1 TiB<br>
**Max. IOPS:** 40-200<br>
**Use Case:** Workloads where data is infrequently accessed<br>


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

