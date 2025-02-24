Provide your solution here: Building Castle In The Cloud
**I. Overview Diagram**
![tai AWS Architecture (2)](https://github.com/user-attachments/assets/e3891377-3f56-42c4-9af5-1affebb3a802)


**II. Elaboration on why each cloud service is used and what are the alternatives considered.**

**1. Infra Layer**
Amazon CloudFront:

- For caching and low-latency delivery.

Elastic Load Balancer (ALB):

- Distributes traffic across application servers in multiple Availability Zones.


**2. Application Layer**
Amazon EKS

- Container orchestration for the trading application with auto-scaling.

Amazon API Gateway:

- Manages API traffic and provides throttling and caching.

**3. Data Layer**
Amazon Aurora (PostgreSQL):

- High-performance relational database with read replicas for scaling.
Amazon EFS:
- Shared File/ Storage 

Amazon ElastiCache (Redis):

- Caching frequent queries and session data for faster response times.

**4. Messaging and Event Handling**
Amazon SQS:

- Decouples services with reliable message queuing.

**5. Security and Networking**
AWS WAF & Shield:

- Protects against DDoS and common web exploits.

Amazon VPC: Isolated network

AWS Secrets Manager:

- Secure storage for API keys and database credentials.

**6. Monitoring and Logging**
Amazon CloudWatch:

- Real-time monitoring, logging, and alerts.


**Scalability Strategy**

1. Frontend Scaling:

- CloudFront scales automatically based on traffic.

- ALB auto-scales across multiple Availability Zones.

2. Application Layer Scaling:

- EKS auto-scales based on CPU/memory usage and request rates.

- API Gateway scales horizontally with incoming API requests.

3. Data Layer Scaling:

- Aurora supports read replicas and auto-scaling storage.

- ElastiCache clusters can be scaled horizontally.

4. Event Handling Scaling:

- SQS supports virtually unlimited message queuing.


**Future Growth Considerations**

1. Microservices Architecture:

- Gradually break down monolithic services into microservices as the product grows.

2. Multi-Region Deployment:

- Deploy in multiple AWS regions for global high availability and disaster recovery.

3. Cost Optimization:

- Use Spot Instances for non-critical workloads.

- Employ AWS Savings Plans and Reserved Instances for predictable workloads.

- Integrate Amazon Redshift for complex analytics on trading data.
