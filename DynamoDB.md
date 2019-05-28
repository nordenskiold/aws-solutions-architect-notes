## Amazon DynamoDB

### Overview
Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single-digit millisecond latency at any scale. It can scale to support petabytes of data and tens of millions of read and write requests per second. It is a fully managed database that supports both document and key-value data models. DynamoDB is designed to run high-performance, internet-scale applications that would overburden traditional relational databases. It is a good fit for mobile, web, gaming, ad-tech, IoT, and many other applications

#### Eventual Consistent vs Strongly Consistent Reads
**Eventual Consistent Reads**<br>
Consistency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (*Best Read Performance*)

**Strongly Consistent Reads**<br>
A strongly consistent read returns a result that reflects all writes that received a successful response prior to the read. If you need to read data that was written within 1 second then you need strongly consistent reads.

### Key Take Aways
- Stored on SSD storage
- Spread across 3 geographically distinct data centers
- Eventual Consistent Reads (default)
- Strongly Consistent Reads