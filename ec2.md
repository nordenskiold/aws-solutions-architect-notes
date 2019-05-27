## Elastic Compute Cloud (EC2)

### Overview
Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

#### EC2 Pricing Tiers

1. **On Demand**
Allows you to pay a fixed rate by the hour (or by the second) with no commitment.

2. **Reserved**
Provides you with a capacity reservation, and offer a significant discount on the hourly charge for an instance. Contract Terms are 1 Year or 3 Year Terms

3. **Spot**
Enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times.

4. **Dedicated Hosts**
Physical EC2 server dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses.

#### On Demand Pricing
**Use Case:**

- Users that want the low cost and flexibility of Amazon Ec2 without any up-front payment or long-term commitment
- Applications with short term, spiky or unpredictable workloads that cannot be interrupted
- Applications being developed or tested on Amazon EC2 for the first time

#### Reserved Pricing
**Use Case:**

- Applications with steady state or predictable usage
- Applications that require reserved capacity
- Users able to make upfront payments to reduce their total computing costs even further

**Types**:

1. **Standard Reserved Instances**
These offer up to 75% off on demand instances. The more you pay up front and the longer the contract, the greater the discount

2. **Convertible Reserved Instances**
These offer up to 54% off on demand capability to change the attributes of the RI as long as the exchange results in the creation of Reserved Instances of equal or greater value

3. **Scheduled Reserved Instances**
These are available to launch withing the time windows you reserve. This option allows you to match your capacity reservation to a predicatable recurring schedule that only requires a fraction of a day, week, or a month.

#### Spot Pricing
**Use Case:**

- Applicatcions that have flexible start and end times
- Applications that are only feasible at very low compute prices
- Users with urgent computing needs for large amounts of additional capacity

#### Dedicated Hosts Pricing
**Use Case:**

- Useful for regulatory requirements that may not support multi-tenant virtualization
- Great for licensing which does not support multi-tenancy or cloud deployments
- Can be purchased On-Demand (hourly).
- Can be purchased as a Reservation for up to 70% off the On-Demand price.

### Key Take Aways
- Amazon Elastic Compute Cloud  (EC2) is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.
- Four different tiers, **On Demand**, **Reserved**, **Spot**, and **Dedicated Hosts**
- If the spot instance is terminated by Amazon EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for any hour in which  the instance ran.

- Termination Protection is **turned off by default**, you must turn it on
- On an EBS-backed instance, **the default action is for the root EBS volume to be deleted** when the instance is terminated
- EBS Root Volumes of your DEFAULT AMI's cannot be encrypted. You can also use a third party tool (such as bit locker etc) to encrypt the root volume, or this can be done when creating AMI's in the AWS console or using the API
- Additional volumes can be encrypted
