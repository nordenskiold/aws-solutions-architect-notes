## API Gateway

### Overview
Amazon API Gateway is a fully managed service that makes it easy for developers to publish, maintain, monitor, secure, and operate APIs at any scale. It's a pay-as-you-go service that takes care of all of the undifferentiated heavy lifting involved in securely and reliably running APIs at scale.

- Expose HTTPS endpoints to define a RESTful API
- Connect to services like Lambda & DynamoDB
- Send each API endpoint to a different target
- Run efficiently with low cost
- Scale effortlessly
- Track and control usage by API key
- Throttle requests to prevent attacks
- Connect to CloudWatch to log all requests for monitoring
- Maintain multiple versions of your API

#### Caching
You cna enable API caching in Amazon API Gateway to cache your endpoint's response. With caching, you can reduce the number of calls made to your endpoint and also improve the latency of the requests to your API. When you enable caching for a stage, API Gateway caches responses from your endpoint for a specified time-to-live (TTL) period, in seconds. API Gateway then responds to the request by looking up the endpoint response from the cache instead of making a request to your endpoint.

#### Same Origin Policy
The same-origin policy is an important concept in the web application security model. Under the policy, a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin. This is done to prevent Cross-Site Scripting (XSS) attacks. Same-origin policy is enforced by web browsers but ignored by some tools like PostMan and curl.

#### Cross Origin Resource Sharing (CORS)
CORS is one way that a server can relax the same-origin policy and allow access from specific (or all) clients. CORS is a machanism that allows restricted resources (e.g. fonts) on a web page to be requested from another domain outside the domain from which the first resource was served.

### Key Take Aways
- Understand API Gateway at a high level
- API Gateway has caching capabilities to increase performance
- API Gateway is low cost and scales automatically
- You can throttle API Gateway to prevent attacks
- You can log results to CloudWatch
- If you are using Javascript that uses multiple domains with API Gateway, ensure that you have enabled CORS on API Gateway
- CORS in enforced by the client