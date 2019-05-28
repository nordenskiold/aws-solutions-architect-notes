## AWS Databases

### Overview
Amazon RDS is a managed relational database service that provides you six familiar database engines to choose from, including Amazon Aurora, MySQL, MariaDB, Oracle, Microsoft SQL Server, and PostgreSQL.

RDS makes it easy to use replication to enhance availability and reliability for production workloads. Using the Multi-AZ deployment option, you can run mission-critical workloads with high availability and built-in automated fail-over from your primary database to a synchronously replicated secondary database. Using Read Replicas, you can scale out beyond the capacity of a single database deployment for read-heavy database workloads.

#### RDS Backups
Whenever you restore either an Automatic Backup or a manual Snapshot, the restored version of the database will be a new RDS instance with a new DNS endpoint.

**Automated Backup**<br>
Automated Backups allow you to recover your database to any point in time within a "retention period". The retention period can be between 1 and 35 days. Automated Backups will take a full daily snapshot and will also store transaction logs throughout the day. When you do a recovery, AWS will first choose the most recent daily back up, and then apply transaction logs relveant to that day. This allows you to do a point in time recovery down to a second, within the retention period.

Automated Backups are enabled by default. The backup data is stored in S3 and you get free storage space equal to the size of your database. So if you have an RDS instance of 10Gb, you will get 10Gb worth of storage. Backups are taken within a defined window. During the backup window, storage I/O may be suspended while your data is being backed up and you may experience elevated latency. 

**Database Snapshots**
DB Snapshots are done manually (user initiated). They are stored even after you delete the original RDS instance, unlike automated backups. 

#### RDS Encryption At Rest
Encryption at rest is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB, and Aurora. Encryption is done using the AWS Key Management Service (KMS). Once your RDS instance is encrypted, the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas, and snapshots.

#### Multi-AZ

**Multi-AZ is for Disaster Recovery Only**<br>
*Automatic failover if one DB goes down*<br>

It is not primarily used for improving performance. For performance improvement, you need Read Replicas.

Multi-AZ allows you to have an exact copy of your production database in another Abailability Zone. AWS handles the replication for you, so when your production database is written to, this write will automatically be synchronized to the stand by database.

In the event of planned database maintenance, DB Instance failure, or an Availability Zone failure, Amazon RDS will automatically failover to the standby so that database operations can resume quickly without administrative intervention.

Multi-AZ is avaialble for SQL Server, Oracle, MySQL Server, PostgreSQL, and mariaDB.

#### Read Replica
**Read replicas are used for *scaling*, not disaster recovery**<br>
***NO** Automatic failover if one DB goes down*<br>
Read replicas allow you to have a read-only copy of your production database. This is achieved by using Asynchronous replication from the primary RDS instance to the read replica. You use read replicas primarily for very read-heavy database workloads.

Read replicas are available for MySQL Server, PostgreSQL, MariaDB, and Aurora

### Key Take Aways
- RDS runs on virtual machines
- You cannot log in to these operating systems however
- Patching of the RDS Operatin System and DB is Amazon's responsibility
- RDS is **NOT** Serverless
- Aurora Serverless **IS** Serverless
- Two different types of backup for RDS; **Automated Backups** and **Database Snapshots**

#### Read Replica Key Take Aways
- Read replicas are used to increase performance
- Must have automatic backups turned on in order to deploy a read replica
- You can have up to 5 read replica copies of any database
- You can have read replicas of read replicas (but this could increase latency)
- Each read replica will have its own DNS end point
- Read replicas can also be Multi-AZ
- You can create read replicas of Multi-AZ source databases
- Read replicas can be promoted to master. This breaks the replication
- Read replicas can be created in different regions (don't have to be the same as master RDS region)

#### Multi-AZ Key Take Aways
- Used for disaster recovery
- Failover from one AZ to another can be forced by rebooting the RDS instance