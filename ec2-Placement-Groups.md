## EC2 Placement Groups
### Overview
When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize correlated failures. You can use placement groups to influence the placement of a group of interdependent instances to meet the needs of your workload. 

#### Types of Placement Groups
**Clustered Placement Group**<br>
A cluster placement group is a grouping of instances within a single Availability Zone. Placement groups are recommended for application that need low network latency, high network throughput, or both. Only certain instances can be launched in to a Clustered Placement Group. Typically, HPC (high performance computing) applications would be placed in a clustered placement group.

**Spread Placement Group**<br>
A spread placement group is a group of instances that are each placed on distinct underlying hardware. Spread placement groups are recommended for applications that have a small number of critical instances that should be kept seperate from each other.

**Partition Placement Group**<br>
A partition placement group spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka.

### Key Take Aways

- A clustered placement group **can't** span multiple Availability Zones
- A spread placement group **can** span multiple Availability Zones
- The name you specify for a placement group must be unique within your AWS account
- Only certain types of instances can be launched in a placement group (Compute Optimized, GPU, Memory Optimized, Storage Optimized)
- AWS recommends homogenous instances within placement groups (e.g. you shouldn't have several different instance types within your placement group)
- You can't merge placement groups
- You can't move an existing instance into a placement group. You can create an AMI from your existing instance, and then launch a new instance from the AMI into a placement group


