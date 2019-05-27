## CloudWatch

### Overview
Amazon CloudWatch is a monitoring and management service that provides data and actionable insights for AWS, hybrid, and on-premises applications and infrastructure resources. With CloudWatch, you can collect and access all your performance and operational data in form of logs and metrics from a single platform. This allows you to overcome the challenge of monitoring individual systems and applications in silos (server, network, database, etc.). CloudWatch enables you to monitor your complete stack (applications, infrastructure, and services) and leverage alarms, logs, and events data to take automated actions and reduce Mean Time to Resolution (MTTR). 

**CloudWatch can monitor things like:**

- Compute
    - EC2 Instances
    - Autoscaling Groups
    - Elastic Load Balancers
    - Eoute53 Health Checks
- Storage and Content Delivery
    - EBS Volumes
    - Storage Gateways
    - CloudFront

**Metrics consist of (amongst other):**

- CPU
- Network
- Disk
- Status Check

#### Monitoring Types
**Standard Monitoring**

- Data is available automatically in 5 Minute periods at no charge.
- Enabled by default for new EC2 instances

**Detailed Monitoring**

- Data is available in 1-minute periods for an additional cost. 
- Must be specifically enabled for an instance
- Can aggregate monitoring data for multiple instances if they all have detailed monitoring enabled

#### Monitoring Tools

- **Dashboards** - Create dashboards to see what is happening in your AWS environment
- **Alarms** - Allows you to set Alarms that notify you when particular thresholds are hit
- **Events** - CloudWatch Events help you respond to state changes in your AWS resources
- **Logs** - CloudWatch Logs help you to aggregate, monitor and store logs

### Key Take Aways
- CloudWatch is used for monitoring performance
- CloudWatch can monitor most of AWS as well as your applications that run on AWS
- CloudWatch with EC2 will monitor events every 5 minutes by default
- You can have 1 minute intervals by turning on detailed monitoring
- You can create CloudWatch alarms which trigger notifications
- CloudWatch is all about performance. CloudTrail is all about auditing.

