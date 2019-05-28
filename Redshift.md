## Amazon Redshift

### Overview
Amazon Redshift is a fast, scalable, fully managed, petabyte-scale data warehouse service in the cloud. You can setup and deploy a new data warehouse in minutes, and run queries across petabytes of data in your Redshift data warehouse, and exabytes of data in your data lake built on Amazon S3. You can start small for just $0.25 per hour and scale to $250 per terabyte per year, less than one-tenth the cost of other solutions.

#### Redshift Compression
Columnar data stores can be compressed much more than row-based data stores because similar data is stored sequentially on disk. Amazon Redshift employs multiple compression techniques and can often achieve significant compression relative to trasitional relational data stores. In addition, Amazon Redshift doesn't require indexes or materialized views, and so uses less space than traditional relational database systems. When loading data into an empty table, Amazon Redshift automatically samples your data and selects the most appropriate compression scheme.

#### Massively parallel Processing (MPP)
Redshift automatically distrivutes data and query load across all nodes. Redshift makes it easy to add nodes to your data warehouse and enables you to maintain fast query performance as your data warehouse grows.

#### Backups
- Enabled by default with a 1 day retention period
- Maximum retenton period is 35 days
- Redshift always attempts to maintain at least three copies of your data (the original and replica on the compute nodes and a backup in S3)
- Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery

#### Pricing
Pricing is based on three aspects. Compute Node Hours, Backups, and Data transfer (only within a VPC, not outside it).

Compute node hours are the total number of hours oyu run across all your compute nodes for the billing period. You are billed for 1 unit per node per hour, so a 3-node data warehouse cluster running persistently for an entire month would incur 2,160 instance hours. You will not be charged for leader node hours; only compute nodes will incur charges.


#### Security Considerations
- Encrypted in transit using SSL
- Encrypted at rest using AES-256 encryption
- By default, Redshift takes care of key management. But you can also manage your own keys through a Hardware Security Module (HSM) or through AWS KMS

#### Availability
Currently, Amazon Redshift only supports Single-AZ deployments. You can run data warehouse clusters in multiple AZ's by loading data into two Amazon Redshift data warehouse clusters in separate AZs from the same set of Amazon S3 input files. With Redshift Spectrum, you can spin up multiple clusters across AZs and access data in Amazon S3 without having to load it into your cluster. In addition, you can also restore a data warehouse cluster to a different AZ from your data warehouse cluster snapshots.

### Key Take Aways
- Redshift is used for buisness intelligence and OLAP (Online Analytical Processing)
- Only supports Single-AZ deployments
- Backups are enabled by default with a 1 day retention policy
- Maximum retention period for backups is 35 days
- Redshift will always attempt to maintain at least three copies of your data (the original and replica on the compute nodes, and a backup in S3)
- Redshift can also asynchronously replicate your snapshots to S3 in another region for disaster recovery
