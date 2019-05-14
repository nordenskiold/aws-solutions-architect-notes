##CloudFront

###Overview
When using CloudFront, requests for your content is automatically routed to the nearest edge location, so content is delivered with the best possible performance. CloudFront is essentially just a content delivery network (CDN).

###Key Take Aways
Cloudfront
- Objects are cached for the life of the TTL (Time to Live)
- You can clear cached objects, but you will be charged

- **Edge Location** - This is the location where content will be cached. Objects can be both read and written to edge locations. An edge location is separate to an AWS Region or AWS Availability Zone
- **Origin** - This is the origin of all the files that the CDN will distribute. This can be an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or  Route53
- **Distribution** - This is the name given the CDN which consists of a collection of Edge Locations 
    - **Web Distribution** - Typically used for websites
    - **RTMP** - Used for Media Streaming
