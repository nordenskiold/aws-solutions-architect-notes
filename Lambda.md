## Lambda

### Overview
AWS Lambda is a serverless compute service that runs your code in response to events and automatically manages the underlying compute resources for you. You can use AWS Lambda to extend other AWS services with custom logic, or create your own back-end services that operate at AWS scale, performance, and security. AWS Lambda can automatically run code in response to multiple events, such as HTTP requests via Amazon API Gateway, modifications to objects in Amazon S3 buckets, table updates in Amazon DynamoDB, and state transitions in AWS Step Functions.

Lambda runs your code on high-availability compute infrastructure and performs all the administration of the compute resources, including server and operating system maintenance, capacity provisioning and automatic scaling, code and security patch deployment, and code monitoring and logging. All you need to do is supply the code.

#### Pricing
Pricing is based on the number of requests and the duration of execution.

**Number of Requests**<br>
First 1 million requests are free. $0.20 per 1 million requests thereafter.

**Duration**<br>
Duration is calculated from the time your code begins executing until it returns or otherwise terminates, rounded up to the nearest 100ms. The price depends on the amount of memory you allocate to your function. You are charged $0.00001667 for every GB-second used.


### Key Take Aways
- Lambda scales out (not up) automatically. Aka. scales horizontally not vertically.
- Lambda functions are independent, 1 event == 1 function
- Lambda is serverless
- Lambda functions can trigger other lambda functions, 1 event can trigger multiple other functions
- Architectures can get extremely complicated, AWS X-ray allows oyu to debug what is happening
