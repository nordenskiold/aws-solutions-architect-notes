## Aurora

### Overview
Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases.

Amazon Aurora is up to five times faster than standard MySQL databases and three times faster than standard PostgreSQL databases. It provides the security, availability, and reliability of commercial databases at 1/10th the cost. 

**General Key Aspects of Aurora**

- Start with 10GB, Scales in 10GB increments to 64TB (Storage Autoscaling)
- Compute resources can scale up to 32 virtual CPUs and 244GB of Memory
- 2 copies of your data is contained in each avilability zone, with a minimum of 3 availability zones. So you will always have 6 copies of your data spread across 3 AZs. Because of this, Aurora is only available in regions with 3 AZs.
- Aurora is designed to transparently handle the loss of up to two copies of data without affecting database write avilability and up to three copies without affecting read availability
- Aurora storage is also self-healing. Data blocks and disks are continously scanned for errors and repaired automatically

#### Aurora Read Replicas
Two types of Read Replicas are available for Aurora

**Aurora Replicas**<br>

- Up to 15 replicas
- Automated failover

**MySQL Read Replicas**<br>

- Up to 5 replicas
- No automated failover

#### Backups

- Automated backups are always enabled of Aurora DB instances. Backups do not impact DB performance
- DB Snapshots can be taken with Aurora; This does not impact performance.
- You can share Aurora Snapshots with other AWS accounts 


### Key Take Aways
- Aurora is Amazon's proprietary database that is compatible with MySQL and PostgreSQL
- You will always have 6 copies of your data; 2 copies of your data in each availability zone with a minimum of 3 availability zones
- Two types of replicas avilable; Aurora and MySQL. Automated failover is **only** available with Aurora Replicas
- Aurora has automated backups turned on by default. You can also take Snapshots with Aurora. You can share these snapshots with other AWS accounts.
