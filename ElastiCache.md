## ElastiCache

### Overview
ElastiCache is a web service that makes it easy to deploy, operate, and scale an in-memory cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying entirely on slower disk-based databases.

Amazon ElastiCache offers fully managed Redis and Memcached. Seamlessly deploy, run, and scale popular open source compatible in-memory data stores. 

#### Memcached vs. Redis


| Requirement | Memcached | Redis  |
| --- |:---------------:| ---------------------------------:|
| Simple Cache to offload DB       |  Yes  | Yes  |
| Ability to scale horizontally       |  Yes  |  No  |
| Multi-threaded performance      |  Yes  |  No  |
| Advanced Data types                 |  No   |  Yes |
| Ranking/Sorting data sets          |  No   |  Yes |
| Pub/Sub capabilities                   |  No   |  Yes |
| Persistence                                 |  No   |  Yes |
| Multi-AZ                                      |  No   |  Yes |
| Backup & Restore Capabilities   |  No   |  Yes |


### Key Take Aways
- Use Elasticache to increase database and web application performance
- Reddis is Multi-AZ
- You can do backups and restores of Reddis
- Use Memcached if you need to scale horizontally
