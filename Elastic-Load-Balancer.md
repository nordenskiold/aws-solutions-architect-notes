## Elastic Load Balancers

### Overview
3 Types of AWS Load Balancers:

**Application Load Balancer (ALB)**<br>
Best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application-aware. They are intelligent, and you can create advanced request routing, sending specified requests to specific web servers.

**Network Load Balancer**<br>
Best suited for load balancing of TCP traffic where extreme performance is required. Operating at the connection level (Layer 4), Network Load Balancer are capable of handling millions of requests per second, while maintaining ultra-low latencies. *Used for performance*

**Classic Load Balancer (ELB)**<br>
Are legacy elastic load balancers. You can load balance HTTP/HTTPS applications and use Layer 7-specific features, such as X-Forwarded-for and sticky sessions. You can also use strict Layer 4 load balancing for applications that rely purely on the TCP protocol.

If your application stops responding, the ELB (Classic Load Balancer) responds with a 504 error. This means that the application is having issues either on the web server or database layer. 

#### X-Forwarded-For Header
The X-Forwarded-For request header helps you identify the IP address of a client when you use an HTTP or HTTPS load balancer. Because load balancers intercept traffic between clients and servers, your server access logs contain only the IP address of the load balancer. To see the IP address of the client, use the X-Forwarded-For request header. Elastic Load Balancing stores the IP address of the client in the X-Forwarded-For request header and passes the header to your server.


#### Sticky Sessions
By default, a Classic Load Balancer routes each request independently to the registered instance with the smallest load. However, you can use the sticky session feature (also known as session affinity), which enables the load balancer to bind a user's session to a specific instance. This ensures that all requests from the user during the session are sent to the same instance.

You can enable Sticky Sessions for ALBs as well, but the traffic will be sent at the Target Group level rather than individual instances.

#### Cross Zone Load Balancing
With cross-zone load balancing, each load balancer node for your Classic Load Balancer distributes requests evenly across the registered instances in all enabled Availability Zones. If cross-zone load balancing is disabled, each load balancer node distributes requests evenly across the registered instances in its Availability Zone only. 

Cross-zone load balancing reduces the need to maintain equivalent numbers of instances in each enabled Availability Zone, and improves your application's ability to handle the loss of one or more instances. However, it is still recommend that you maintain approximately equivalent numbers of instances in each enabled Availability Zone for higher fault tolerance.

For environments where clients cache DNS lookups, incoming requests might favor one of the Availability Zones. Using cross-zone load balancing, this imbalance in the request load is spread across all available instances in the region, reducing the impact of misbehaving clients.

#### Path Patterns
You can create a listener with rules to forward requests based on the URL path. This is known as path-based routing. If you are running microservices, you can route traffic to multiple back-end services using path-based routing. For example, you can route general requests to one target group and requests to render images to another target group.

### Key Take Aways
- Know the three types of load balancers and their differences. Application Load Balancer, Network Load Balancer and Classic Load Balancer (ELB).
- 504 Error means that the gateway has timed. This means that the application is not responding within the idle timeout period. You will need to troubleshoot and figure out if its the web server or database server.
- If you need the IPv4 address of your end user, look for the **X-Forwarded-For** header
- Instances monitored by ELB are reported as InService, or OutofService
- Health Checks check the instance health by talking to it
- Load Balancers have their own DNS name. You are never given an IP address
- Sticky sessions enable your users to stick to the same EC2 instance. Can be useful if you are storing information locally to that instance.
- Cross Zone Load Balancing enables you to load balance across multiple availability zones.
- Path patterns allow you to direct traffic to different EC2 instances based on the URL contained in the request
