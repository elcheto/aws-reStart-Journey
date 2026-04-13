## Introduction

I’m excited to walk you through the technical foundation of our next-generation 3D E-Commerce platform. In the world of 3D retail, the biggest enemy is latency. If a 3D model takes ten seconds to load, we lose the customer. Therefore, we have designed this architecture on AWS to be global, resilient, and incredibly fast. Our design follows the five pillars of the AWS Well-Architected Framework: Reliability, Security, Performance, Cost, and Operational Excellence.

## 3D E-Commerce Platform Architecture on AWS

<img width="750" height="540" alt="3D E-commerce" src="https://github.com/user-attachments/assets/8c82e961-6f04-4286-b022-5f6e7f753cb0" />


### Phase 1: The Global Edge & Security Layer
"When a user types our URL into their browser, the journey begins at Amazon Route 53. We chose this not just for DNS, but for its Latency-based Routing capabilities—directing users to the AWS region that will give them the fastest experience.

To handle our massive 3D files—like high-poly furniture models—we’ve implemented Amazon CloudFront. By using a Global Content Delivery Network (CDN), we move the 'heavy lifting' away from our origin servers and store it at Edge Locations. This ensures that the 3D 'spin-and-zoom' experience is buttery smooth, regardless of the user’s physical location.

For security, we’ve placed AWS WAF and AWS Shield at the very edge. This allows us to inspect incoming web requests and filter out malicious traffic like SQL injection or automated scrapers before they ever reach our internal network, effectively neutralizing threats at the perimeter."

### Phase 2: The Compute & High-Availability Engine
"As we move into the Application Tier, you’ll see our Multi-AZ (Availability Zone) strategy. We use an Application Load Balancer (ALB) to act as the traffic conductor. It constantly performs health checks; if one server instance becomes unresponsive, the ALB immediately reroutes traffic to a healthy one, ensuring 24/7 uptime.

Our core logic runs on Amazon EC2 within an Auto Scaling Group. In e-commerce, traffic is never a flat line. During a product launch or a holiday sale, Auto Scaling detects the rise in CPU demand and spins up new instances in minutes. When traffic drops, it terminates those instances, ensuring we never pay for idle hardware.

To complement this, we’ve integrated AWS Lambda. We use Lambda for 'short-lived' tasks like processing image uploads or sending transactional emails. This serverless approach is highly cost-efficient because we are billed only for the milliseconds the code is actually running."

### Phase 3: Data Strategy & The Storage Warehouse
"Our data strategy is divided into three specialized areas to prevent bottlenecks:

Amazon S3: This is our 'Source of Truth' for all static content. S3 provides unmatched durability. We use S3 Intelligent-Tiering here to automatically move older product models to cheaper storage tiers after they haven't been accessed for 30 days, optimizing our costs without human intervention.

Amazon Aurora (RDS): For our product catalog and financial transactions, we needed the power of a relational database. We chose Aurora because it provides up to five times the throughput of standard MySQL. It handles complex queries—like 'show me all red chairs currently in stock'—with ease.

Amazon DynamoDB: For the shopping cart and user session state, speed is everything. DynamoDB provides single-digit millisecond performance at any scale. By offloading session data to DynamoDB, we keep our Aurora database lean and focused on critical order processing."

### Phase 4: Governance & Continuous Optimization
"Finally, we maintain total control through our Management Tier. AWS IAM (Identity and Access Management) ensures the 'Principle of Least Privilege'—nobody has more access than they need. All sensitive customer data is encrypted using keys managed by AWS KMS.

We use Amazon CloudWatch for real-time observability. It doesn't just show us graphs; it triggers the automation that keeps our site alive. And lastly, we utilize AWS Trusted Advisor, which acts as a constant auditor, scanning our environment to find security gaps or opportunities to save money by identifying underutilized resources."

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
