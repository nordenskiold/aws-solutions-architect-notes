## Amazon Machine Image (AMI)

### Overview
An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.

An AMI includes the following:

- One or more EBS snapshots, or, for instance-store-backed AMIs, a template for the root volume of the instance (for example, an operating system, an application server, and applications).
- Launch permissions that control which AWS accounts can use the AMI to launch instances.
- A block device mapping that specifies the volumes to attach to the instance when it's launched.

You can select your AMI based on:

- Region 
- Operating system
- Architecture (32-bit or 64-bit)
- Launch Permissions
- Storage for the Root Device (Root Device Volume)
    - Instance Store (ephermal storage)
    - EBS Backed Volume
    
 All AMIs are categorized as either backed by Amazon EBS or backed by instance store.
 
 **For EBS Volumes:** The root device for an instance launched from the AMI is  an Amazon EBS volume created from an Amazon EBS snapshot.
 
 **For Instance Store Volumes:** The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon  S3.

#### EBS vs. Instance Store Volumes
An Instance Store Volume is a disk that is physically attached to the virtualization host. Because of this, it offers the lowest latency storage available to an instance and therefore the highest IOPS. 

An EBS backed volume is storage on a remote networked connected NAS and may be competing for I/O with multiple other instances. Because of this, latency **may** be higher and IOPS **may** be lower.

You can think of the difference between the two as Instance Store Volume being RAM, and EBS being a traditional harddrive. The former offers greater IOPS but has the drawback of being volatile. The latter offers lesser IOPS but has the advantage of being persistent.


| | EBS backed | Instance Store backed  |
| --- |:---------------:| -----------------------------:|
| **Pros**      | **+** Resilient  | **+** Highest possible IOPS<br>**+** Lowest possible latency |
| **Cons**      | **-** May have lower IOPS<br> **-** May have greater latency     |   **-** Ephemeral nature means the data could be lost |



### Key Take Aways
- Instance Store Volumes are sometimes called Ephemeral Storage
- Instance store volumes cannot be stopped. If the underlying host fails, you will lose your data
- EBS backed instances can be stopped. You will not lose the data on this instance if it is stopped
- You can reboot both, you will not lose your data
- By default, both **root** volumes will be deleted on termination. However, with EBS volumes, you can tell AWS to keep the root device volume
