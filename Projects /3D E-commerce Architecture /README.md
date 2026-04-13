## 3D E-Commerce Platform Architecture on AWS

<img width="750" height="540" alt="3D E-commerce" src="https://github.com/user-attachments/assets/8c82e961-6f04-4286-b022-5f6e7f753cb0" />


## AWS Services used and Why we chose each AWS service:

**Networking & Traffic Management**
1. **Amazon Route 53**: Managed DNS (Domain Name System) service.
<br> Why it’s used: Routes global users to the correct region.
<br> Supports latency-based or failover routing for high availability.
<br> Ensures users reach the closest healthy endpoint.

3. **Amazon CloudFront**: Content Delivery Network (CDN).
<br> Why it’s used: Caches static and dynamic content at edge locations.
<br> Reduces latency for global users.
<br> Improves performance and reduces load on backend servers.

4. **Elastic Load Balancing (ELB)**: Distributes incoming traffic across multiple servers.
<br> Why it’s used: Prevents single-server overload.
<br> Increases availability and fault tolerance.
<br> Works with Auto Scaling groups.

**Compute Layer**

4. **Amazon EC2**: Virtual servers in the cloud.
<br> Why it’s used: Hosts application services.
<br> Provides scalable compute power.
<br> Runs in multiple Availability Zones for resilience.

5. **AWS Lambda**: Serverless compute service.
<br> Why it’s used: Runs event-driven tasks without managing servers.
<br> Ideal for background jobs, microservices, and automation.
<br> Reduces operational overhead.

6. **EC2 Auto Scalin**g: Automatically adjusts EC2 capacity.
<br> Why it’s used: Scales out during high traffic.
<br> Scales in during low demand to save cost.
<br> Maintains application performance.

**Storage & Databases**

7. **Amazon S3**: Object storage service.
<br> Why it’s used: Stores static assets (images, videos, backups).
<br> Highly durable and scalable.
<br> Works well with CloudFront for content delivery.

8. **Amazon Aurora**: Managed relational database (MySQL/PostgreSQL compatible).
<br> Why it’s used: Stores structured transactional data.
<br> High performance and automatic failover.
<br> Suitable for e-commerce orders, payments, users.

9. **Amazon DynamoDB**: Fully managed NoSQL database.
<br> Why it’s used: Handles high-speed, large-scale key-value data.
<br> Low latency at any scale.
<br> Ideal for sessions, carts, metadata.

**Security & Protection**

10. **AWS Shield**: DDoS protection service.
<br> Why it’s used: Protects applications from distributed denial-of-service attacks.

11. **AWS WAF**: Web Application Firewall.
<br> Why it’s used: Protects against SQL injection, XSS, and common web exploits.
<br> Filters malicious HTTP requests.

12. **AWS Identity and Access Management (IAM)**: Access control management.
<br> Why it’s used: Manages user permissions and roles.
<br> Ensures least-privilege access across services.

13. **AWS Key Management Service (KMS)**: Encryption key management.
<br> Why it’s used: Encrypts data at rest and in transit.
<br> Secures databases and storage.

**Monitoring & Optimization**

14. **Amazon CloudWatch**: Monitoring and logging service.
<br> Why it’s used: Tracks performance metrics.
<br> Sets alarms for failures or high usage.
<br> Centralized logging.

15. **AWS Trusted Advisor**: Best-practice recommendation service.
<br> Why it’s used: Improves cost optimization.
<br> Enhances security and performance.
<br> Identifies underutilized resources.

## How our architecture meets each of the 5 requirements:

1. **High Availability**: This is achieved by distributing traffic globally across multiple regions and by deploying resources in multiple Availability Zones.

2. **Scalability**: This is achieved by implementing EC2 Auto Scaling which automatically adjusts EC2 capacity to handle unpredictable spikes in traffic.

3. **Performance**: Performance is improved with  AWS CloudFront which caches static and dynamic content at edge locations, reducing latency for global users. 

4. **Security:** This is achieved by implementing IAM best practices. AWS Shield and WAF are also used for protection against DDoS(distributed denial-of-service attacks) and as a firewall, respectively. 

5. **Cost Optimization: This is achieved by**:
  - Optimized Amazon EC2 with Auto Scaling; Amazon CloudWatch metrics help us choose the right instance size. 
  - AWS Lambda is used for background jobs, asynchronous processing and APIs.
  - Optimized S3 by enabling lifecycle policies and S3 intelligent-tiering.
  - AWS Trusted Advisor reviews are used to detect underutilised EC2 instances and unattached EBS volumes.

## Challenges:
We faced challenges while implementing our application globally and maintaining the budget, but with the help of Auto Scaling, CloudFront and Route 53, as well as other services, we were able to overcome these challenges.
