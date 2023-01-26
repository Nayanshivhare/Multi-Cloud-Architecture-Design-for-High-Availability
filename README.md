## Multi-Cloud-Architecture-Design-for-High-Availability
### In this architecture I have designed Multi-cloud Hybrid cloud architecture for the Health care organization.
  <img src="https://user-images.githubusercontent.com/66699491/214771251-46ec9d48-7363-4084-990d-91ab1d9e7072.png" width="500" height="300">

  <img src="https://user-images.githubusercontent.com/66699491/214771343-8b39e203-1e33-4f16-aff6-cb10bf13ab19.png" width="500" height="300">



### Business Challenge
Hospital based in USA wants to migrate data center to the cloud. And, according to their requirement they want 99.999% of availability, data privacy, and high security. Data breach can be catastrophic to the organization and put them completely out of business. Based on their goals I am designing a solution that is Highly Available and Highly secure over the  multi-hybrid-cloud infrastrucuture.

### Requirement
* Required the system with 99.99% availability, and 99.999% will be better.
* Required E-health record and Entry system to access the same record at the same time.
* All the records must stay for 7 years and should not be modified.
* E-Health Record:
  * Contain information about patient records.
  * Running all time, with no latency difference.
  * Minimum of 5 servers. 
* Entry System:
  * Used to prescribe the medication, order labs.
  * Low latency, Running all time.
  * Minimum of 5 servers 
* Database:
  * Require a Relational Database that will mission critical, and used widely.
  * 4 x times Read traffic than Write traffic.
  * Scalable and Highly Available.
* Chat program:
  * Doctors will chat within the organization about patient condition.
  * In certain cases, the patient can also communicate with doctors.

### Solution
The first thing we need to do is plan out a **High Availability solution** that is **highly secure**. I would propose to have a **Multi-Cloud environment** because one cloud is a single point of failure despite the guarantee offered by cloud vendors. We can choose AWS and Azure as they are widely used and the most reliable currently in the market. For High Availability, we will have **four direct connect lines two with each cloud vendor**, plus **two VPN backup connections one with each cloud**. As we understand data privacy is the topmost priority and high availability we will use the **next generational firewall from Cisco**. For the database, we will use a Relational Database and NoSql Database. Network File System to share data between E-Health records and entry systems with persistent access to files and information. We will perform Lift and shift to move on-prem to the cloud. Keeping a multi-cloud strategy while designing we made sure to reduce the number of vendor-specific flagship services which will give us complete control over our infrastructure it will make our infrastructure agile and give us the flexibility to move out in case of cloud providers start price hikes.

### Solution Component: 
#### Connectivity
* Internet Service Provider - We are using 2 Internet service providers on two different routers with multiple power sources giving us a robust and highly available internet connection.
* Direct Connect - For achieving 99.999% availability we are using 4 direct connect, 2 with each AWS and Azure. It will reduce the single point of failure. 
* VPN- We are setting a backup line over VPN from our Hospital to AWS and Azure. And Between VPN and Azure.

#### Computational and Database 
* Servers - we will be using 5 servers to run 24x7 as our minimum requirement. 
  * AWS- EC2. 
  * Azure- Virtual Machine.

* Auto Scaling - Based on utilization we will scale up and down using Auto Scaling Group making our infrastructure highly available. 
  * AWS- Auto Scaling Group.
  * Azure- Auto Scaling.

* Load Balancer- To load share between all the running servers equally. It will provide ultra-high performance and low latency.
  * AWS- Network Load Balancer.
  * Azure- Azure Load Balance.

* Network File System - To provide a persistent, fast, and cost-effective solution to access the same files between the E-Health Record Application stack and Entry System Application Stack.
  * AWS - EFS(Elastic File System).
  * Azure - Azure Files.
  
* Relational Database- For E-Health Record and Entry system we will be using a relational MySQL Database so that we can find relations between our stored items, and to increase performance we will be using 2 Read replicas as it is a read-intensive workload. And, we have Hot Standby in case of failure.
  * AWS- RDS EC2 Instance.
  * Azure- RDS Virtual Machine.

* Non-Relational Database- For our chat system, we will be using NoSql Database as it can be cheaper and it will store all kinds of data from pictures to messages. 
  * AWS- NoSql DB EC2 Instance.
  * Azure- NoSql Virtual Machine.

* Caching- It will increase performance for the data that is frequently accessed by storing it in cache memory. It will give us higher throughput and lower latency.
  * AWS- ElasticCache(Redis).
  * Azure- Azure Cache(Redis).
  
* Object Storage- For data backup and long-term data storage. It will be cost-effective and highly available. With the Life cycle policy, we can move data from one Class to another in order to reduce storage cost and delete it after 7 years automatically. 
  * AWS - Simple Storage Service (S3) 
  * Azure- Azure Blob
  
#### Security and Monitoring
 
* Denial Of Service Attack Protection- It is a most common attack that will flood our servers with traffic and make them unavailable or increase costs. In order to prevent that we will use DDOS attack protection.
  * AWS- AWS Shield.
  * Azure - DDoS Protection
  
* Next-Generation Firewall - our perimeter of the network will be protected using a nextgen firewall that will provide us highly secure network and prevent malicious attacks. 
  * AWS- Pal Alto Firewall.
  * Azure- Azure Firewall
 
* Network Access Control List- It will provide security at the subnet level, we can set our rules and keep unwanted traffic out.
  * AWS- NACL(Network Access Control List).
  * Azure- Network Security Groups.

* Security Group- It will be a server-level firewall or security that will protect servers' parameters, based on the rules it will allow traffic to the server.
  * AWS- Security Group.  
  
* Patching: To auto- update our software and prevent any vulnerabilities.
  * AWS- Patch Manager.
  * Azure- Update Management.

* Microsoft AD- For user Management and devices in the hospital we will use this.
  * AWS- Microsoft Managed AD 
  * Azure- Azure Active Directory

* Encryption: We will encrypt our database using AES 256-bit encryption so that no one can see our data in case of any security breach.

* Monitoring and Logs: For watching our logs in real-time and remediate immediately if anything malicious is detected in our logs.
  * AWS- Cloud Watch.
  * Azure- Network Watcher Azure.
  
* Business Intelligent tool for data analysis. It will give us insight into our data and provide us with real-time analysis.
  * AWS - Elastic Search.
  * Azure- Data Explorer Cluster
  
  ![image](https://user-images.githubusercontent.com/66699491/214771154-6721bef8-5147-460a-bc34-56b0022a5cbd.png)
![image](https://user-images.githubusercontent.com/66699491/214771181-41c76b63-6c32-47c9-8b34-6c24181a2ca5.png)
![image](https://user-images.githubusercontent.com/66699491/214771212-2cd7a266-818e-4658-b9f6-0c1ce08dddc2.png)

 

