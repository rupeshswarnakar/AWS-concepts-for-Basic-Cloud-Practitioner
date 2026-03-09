## AWS-concepts-for-Basic-Cloud-Practitioner

### Chapter 1: Intro to Cloud Computing

a. Client-server model: 
  Customer make a request and with permission, server receives, prcoesses and respond to the request. 

b. Cloud Deployment Types:
  - Cloud based
  - On-premise
  - Hybrid

🧠 On-demand deliver --> over internet --> pay-as-you-go

c. Benefits of AWS:
  - Trade fixed expense for variable expense
  - Benefits from massive economics of scale
  - Stop guessing capacity
  - Increase speed and agility
  - Stop spending money running & maintaining data centers
  - Go global in minutes

d. AWS Global Infrastructure:
  - Distribute resources across multiple availability zones, so even one data center fails, others are still running.
  - No interruption.
  - Provide benefits such as high availability and fault tolerance.

e. Shared Responsibility:
  AWS - security of cloud 
  Customer - security in cloud

  🧠 Customer are responsible for managing security configurations and patches for OS running in the cloud.

### Chapter 2: Compute in the Cloud

a. Amazon Elastic Compute Cloud (EC2):
- Amazon EC2 is an AWS service that provides computing power through virtual machines/servers without owing a physical hardware or an infrastructure.
- EC2 Instance is an actual virtual machine/server that is used to run application on, using CPU, memory, storage and network.
- Hypervisor is a software that creates and manage virtual machines/servers by allowing multiple operating systems to share the same physical hardware.
- Multi-tenancy is a cloud model where multiple customers share the same physical insfrastructure with their data & workloads bering logically isolated and secured.

🧠 Hypervisor enables multi-tenancy, EC2 provides the services, EC2 instance are virtual serverr/machines you actually use.

b. How EC2 works:
  Amazon Machine Image (AMI) desfines OS and types of Instances.
  Launch --> Connect --> Use

c. Amazon EC2 Instance types:
  - General Purpose:
      For general computing power, web servers, code repositories. For "Not Sure" scenario.
  - Compute Optimized:
      High performance computing (HPC), gaming servers, scientific models, ML tasks.
  - Memory Optimized;
      Memomry intensive workloads, processing large datasets.
  - Accelerated Comptuing:
      Hardware accelerator, floating point numbers calculation, graphical processing, data pattern match.
  - Storage Computing:
      High performance on locally stored data, data warehousing, I/O intersive app

🧠 Bigger Instance = Bigger Cost

d. How to provision AWS Resources:
  - Amazon Management Console: uses GUI, check billing, web-interface
  - AWS Command Line Interface (CLI): Commands, uses automation and scripting
  - AWS SDK (Software development kit): Use programming language
    
🧠 All interactions with AWS services are powered by APIs (Application Programming Interfaces)

e. Demo of Launching AWS EC2 Instance:

AMI --> Instance type --> Key pair --> Network setting --> Storage --> User data --> Launch 🚀

f. Amazon EC2 pricing:
  - On Demand:
      Pay for what you use, not sure, get all basic compute, storage, memory and network.
  - Saving plans:
      Commit usage level and get 72 % off the On-demand. Commit for 1-3 years.
  - Reserved Instance (RI):
      Steady workload with predictable usuage, commit 1-3 years, get 75 % off the On-demand.
  - Spot Instance:
      Bid on spare instances, but there will be interruption when AWS reclaim that instance, up to 90 % off the On-demand.
  - Dedicated Host:
      Booking entire physical server for security sensitive workload.
  - Dedicated Instance:
      Booking only EC2 instance that run on physical hardware not shared with anyone. This is helpful when you don't want to book entire physical server.

🧠 If you know your workload is going to be steady with predicatable workload, then Reserved Instance flexibilty is best way to optimize cost.

g. Scalibility vs Elasticity:
  - Scalibility = systems' potential to grow overtime.
  - Elasticity = dynamic, on-demand adjustment of resources.

Scale up: Vertical scaling, increasing power of single instance. Not useful everywhere.
Scale out; Horizontal scaling, add more machines/instances.

🧠 The usage level of memory to decide scale in or out is watched by Amazon Cloud watch.

h. Autoscaling:
By deciding minimum, desired and maximum capacity required for business to run smoothly, auto scaling increase or decrease EC2 instances to handle workload per need of business.

i. Elastic Load Balancing (ELB):
Load balancer distributes network trafficking to instances to improve application scalibility. This phenomenon is called as ELB. This is just like a person in Costco who directs customers to 
available registers so that open cashier and ready-to-checkout-customer don't have to worry about finding each other.

ELB handles traffic to distribute them to right EC2 instance by,
- Round Robin (1,2,3,1,2,3...)
- Least Connection (less busy server)
- IP hash (same server for sensitive task)
- Least response time (when different speed servers available for different speed requiring tasks)

🧠 If there is need of more load balancers, then AWS auto scale ELB to handle incoming traffic. 

j. Messaging and Queuing:
This concept is related to cloud communication.

* Tightly coupled architecture: This is related to connection of applications being direct to each other, which if one application is down will imapct other applications directly.

  Application A -----> Application B
  
* Loosely coupled architecture: This is related to connection of applications being independent of each other, which if one application is down will not imapct other applications.

  Application A ----->|Message Queue|-----> Application B

k. Types of Message & Queue:
  - EventBridge:
      Serverless services that connect all the event loosely hence others aren't impacted if one is.
      For eg., if you place order on doordash then payment, order notice, delivery etc. has to be performed. Among these events, if one is impacted then others should run smoothly
  - Amazon simple queue service ( Amazon SQS):
      Messaing and queuing service for cloud communication.
      For eg., when coffee shop receives multiple order then if barista is busy handling other task, then those order stays in queue without needing immediate attention.
  - Amazon simple notification service ( Amazon SNS):
      Public subscribe service. Publishers send messages to their subscribers thorugh SNS topics.
      For eg., a marketing compoany ccan send new items, discount offers, new updates on policies, all these emails separately dedicating to right customers through Amazon SNS.

## Practice Questions
```
AWS allows users to manage their resources using a web based user interface. What is the name of this interface?

A. AWS CLI.
B. AWS API.
C. AWS SDK.
D. AWS Management Console.
Answer
Correct answer: D

Which of the following is an example of horizontal scaling in the AWS Cloud?

A. Replacing an existing EC2 instance with a larger, more powerful one.
B. Increasing the compute capacity of a single EC2 instance to address the growing demands of an application.
C. Adding more RAM capacity to an EC2 instance.
D. Adding more EC2 instances of the same size to handle an increase in traffic.
Answer
Correct answer: D

You have noticed that several critical Amazon EC2 instances have been terminated. Which of the following AWS services would help you determine who took this action?

A. Amazon Inspector.
B. AWS CloudTrail.
C. AWS Trusted Advisor.
D. EC2 Instance Usage Report.
Answer
Correct answer: B

Which of the below options are related to the reliability of AWS? (Choose TWO)

A. Applying the principle of least privilege to all AWS resources.
B. Automatically provisioning new resources to meet demand.
C. All AWS services are considered Global Services, and this design helps customers serve their international users.
D. Providing compensation to customers if issues occur.
E. Ability to recover quickly from failures.
Answer
Correct answer: B, E

Which statement is true regarding the AWS Shared Responsibility Model?

A. Responsibilities vary depending on the services used.
B. Security of the IaaS services is the responsibility of AWS.
C. Patching the guest OS is always the responsibility of AWS.
D. Security of the managed services is the responsibility of the customer.
Answer
Correct answer: A

You have set up consolidated billing for several AWS accounts. One of the accounts has purchased a number of reserved instances for 3 years. Which of the following is true regarding this scenario?

A. The Reserved Instance discounts can only be shared with the master account.
B. All accounts can receive the hourly cost benefit of the Reserved Instances.
C. The purchased instances will have better performance than On-demand instances.
D. There are no cost benefits from using consolidated billing; It is for informational purposes only.
Answer
Correct answer: B

A company has developed an eCommerce web application in AWS. What should they do to ensure that the application has the highest level of availability?

A. Deploy the application across multiple Availability Zones and Edge locations.
B. Deploy the application across multiple Availability Zones and subnets.
C. Deploy the application across multiple Regions and Availability Zones.
D. Deploy the application across multiple VPC’s and subnets.
Answer
Correct answer: C

What does AWS Snowball provide? (Choose TWO)

A. Built-in computing capabilities that allow customers to process data locally.
B. A catalog of third-party software solutions that customers need to build solutions and run their businesses.
C. A hybrid cloud storage between on-premises environments and the AWS Cloud.
D. An Exabyte-scale data transfer service that allows you to move extremely large amounts of data to AWS.
E. Secure transfer of large amounts of data into and out of the AWS.
Answer
Correct answer: A, E

A company has an AWS Enterprise Support plan. They want quick and efficient guidance with their billing and account inquiries. Which of the following should the company use?

A. AWS Health Dashboard.
B. AWS Support Concierge.
C. AWS Customer Service.
D. AWS Operations Support.
Answer
Correct answer: B

A Japanese company hosts their applications on Amazon EC2 instances in the Tokyo Region. The company has opened new branches in the United States, and the US users are complaining of high latency. What can the company do to reduce latency for the users in the US while minimizing costs?

A. Applying the Amazon Connect latency-based routing policy.
B. Registering a new US domain name to serve the users in the US.
C. Building a new data center in the US and implementing a hybrid model.
D. Deploying new Amazon EC2 instances in a Region located in the US.
Answer
Correct answer: D

An organization has a large number of technical employees who operate their AWS Cloud infrastructure. What does AWS provide to help organize them into teams and then assign the appropriate permissions for each team?

A. IAM roles.
B. IAM users.
C. IAM user groups.
D. AWS Organizations.
Answer
Correct answer: C

A company has decided to migrate its Oracle database to AWS. Which AWS service can help achieve this without negatively impacting the functionality of the source database?

A. AWS OpsWorks.
B. AWS Database Migration Service.
C. AWS Server Migration Service.
D. AWS Application Discovery Service.
Answer
Correct answer: B

Adjusting compute capacity dynamically to reduce cost is an implementation of which AWS cloud best practice?

A. Build security in every layer.
B. Parallelize tasks.
C. Implement elasticity.
D. Adopt monolithic architecture.
Answer
Correct answer: C

What are the benefits of having infrastructure hosted in AWS? (Choose TWO)

A. Increasing speed and agility.
B. There is no need to worry about security.
C. Gaining complete control over the physical infrastructure.
D. Operating applications on behalf of customers.
E. All of the physical security and most of the data/network security are taken care of for you.
Answer
Correct answer: A, E

What is the advantage of the AWS-recommended practice of "decoupling" applications?

A. Allows treating an application as a single, cohesive unit.
B. Reduces inter-dependencies so that failures do not impact other components of the application.
C. Allows updates of any monolithic application quickly and easily.
D. Allows tracking of any API call made to any AWS service.
Answer
Correct answer: B

Which of the following helps a customer view the Amazon EC2 billing activity for the past month?

A. AWS Budgets.
B. AWS Pricing Calculator.
C. AWS Systems Manager.
D. AWS Cost & Usage Reports.
Answer
Correct answer: D

What do you gain from setting up consolidated billing for five different AWS accounts under another master account?

A. AWS services’ costs will be reduced to half the original price.
B. The consolidated billing feature is just for organizational purpose.
C. Each AWS account gets volume discounts.
D. Each AWS account gets five times the free-tier services capacity.
Answer
Correct answer: C

What should you do in order to keep the data on EBS volumes safe? (Choose TWO)

A. Regularly update firmware on EBS devices.
B. Create EBS snapshots.
C. Ensure that EBS data is encrypted at rest.
D. Store a backup daily in an external drive.
E. Prevent any unauthorized access to AWS data centers.
Answer
Correct answer: B, C

One of the most important AWS best-practices to follow is the cloud architecture principle of elasticity. How does this principle improve your architecture’s design?

A. By automatically scaling your on-premises resources based on changes in demand.
B. By automatically scaling your AWS resources using an Elastic Load Balancer.
C. By reducing interdependencies between application components wherever possible.
D. By automatically provisioning the required AWS resources based on changes in demand.
Answer
Correct answer: D

A startup company is operating on limited funds and is extremely concerned about cost overruns. Which of the below options can be used to notify the company when their monthly AWS bill exceeds $2000? (Choose TWO)

A. Setup a CloudWatch billing alarm that triggers an SNS notification when the threshold is exceeded.
B. Configure the Amazon Simple Email Service to send billing alerts to their email address on a daily basis.
C. Configure the AWS Budgets Service to alert the company when the threshold is exceeded.
D. Configure AWS CloudTrail to automatically delete all AWS resources when the threshold is exceeded.
E. Configure the Amazon Connect Service to alert the company when the threshold is exceeded.
Answer
Correct answer: A, C

What does Amazon CloudFront use to distribute content to global users with low latency?

A. AWS Global Accelerator.
B. AWS Regions.
C. AWS Edge Locations.
D. AWS Availability Zones.
Answer
Correct answer: C

What does the "Principle of Least Privilege" refer to?

A. You should grant your users only the permissions they need when they need them and nothing more.
B. All IAM users should have at least the necessary permissions to access the core AWS services.
C. All trusted IAM users should have access to any AWS service in the respective AWS account.
D. IAM users should not be granted any permissions; to keep your account safe.
Answer
Correct answer: A

Which of the following does NOT belong to the AWS Cloud Computing models?

A. Platform as a Service (PaaS).
B. Infrastructure as a Service (IaaS).
C. Software as a Service (SaaS).
D. Networking as a Service (NaaS).
Answer
Correct answer: D

The identification process of an online financial services company requires that new users must complete an online interview with their security team. The completed recorded interviews are only required in the event of a legal issue or a regulatory compliance breach. What is the most cost-effective service to store the recorded videos?

A. S3 Intelligent-Tiering.
B. AWS Marketplace.
C. Amazon S3 Glacier Deep Archive.
D. Amazon EBS.
Answer
Correct answer: C

Which service provides DNS in the AWS cloud?

A. Route 53.
B. AWS Config.
C. Amazon CloudFront.
D. Amazon EMR.
Answer
Correct answer: A

Hundreds of thousands of DDoS attacks are recorded every month worldwide. What service does AWS provide to help protect AWS Customers from these attacks? (Choose TWO)

A. AWS Shield.
B. AWS Config.
C. Amazon Cognito.
D. AWS WAF.
E. AWS KMS.
Answer
Correct answer: A, D

A company is deploying a new two-tier web application in AWS. Where should the most frequently accessed data be stored so that the application’s response time is optimal?

A. AWS OpsWorks.
B. AWS Storage Gateway.
C. Amazon EBS volume.
D. Amazon ElastiCache.
Answer
Correct answer: D

You want to run a questionnaire application for only one day (without interruption), which Amazon EC2 purchase option should you use?

A. Reserved instances.
B. Spot instances.
C. Dedicated instances.
D. On-demand instances.
Answer
Correct answer: D

You are working on a project that involves creating thumbnails of millions of images. Consistent uptime is not an issue, and continuous processing is not required. Which EC2 buying option would be the most cost-effective?

A. Reserved Instances.
B. On-demand Instances.
C. Dedicated Instances.
D. Spot Instances.
Answer
Correct answer: D

Which of the following can be described as a global content delivery network (CDN) service?

A. AWS VPN.
B. AWS Direct Connect.
C. AWS Regions.
D. Amazon CloudFront.
Answer
Correct answer: D

Which of the following services allows customers to manage their agreements with AWS?

A. AWS Artifact.
B. AWS Certificate Manager.
C. AWS Systems Manager.
D. AWS Organizations.
Answer
Correct answer: A

Which of the following are examples of AWS-Managed Services, where AWS is responsible for the operational and maintenance burdens of running the service? (Choose TWO)

A. Amazon VPC.
B. Amazon DynamoDB.
C. Amazon Elastic MapReduce.
D. AWS IAM.
E. Amazon Elastic Compute Cloud.
Answer
Correct Answer: B, C

Your company has a data store application that requires access to a NoSQL database. Which AWS database offering would meet this requirement?

A. Amazon Aurora.
B. Amazon DynamoDB.
C. Amazon Elastic Block Store.
D. Amazon Redshift.
Answer
Correct answer: B

As part of the Enterprise support plan, who is the primary point of contact for ongoing support needs?

A. AWS Identity and Access Management (IAM) user.
B. Infrastructure Event Management (IEM) engineer.
C. AWS Consulting Partners.
D. Technical Account Manager (TAM).
Answer
Correct answer: D

How can you view the distribution of AWS spending in one of your AWS accounts?

A. By using Amazon VPC console.
B. By contacting the AWS Support team.
C. By using AWS Cost Explorer.
D. By contacting the AWS Finance team.
Answer
Correct answer: C

Which of the following must an IAM user provide to interact with AWS services using the AWS Command Line Interface (AWS CLI)?

A. Access keys.
B. Secret token.
C. UserID.
D. User name and password.
Answer
Correct answer: A

You have AWS Basic support, and you have discovered that some AWS resources are being used maliciously, and those resources could potentially compromise your data. What should you do?

A. Contact the AWS Customer Service team.
B. Contact the AWS Abuse team.
C. Contact the AWS Concierge team.
D. Contact the AWS Security team.
Answer
Correct answer: B

Select TWO examples of the AWS shared controls.

A. Patch Management.
B. IAM Management.
C. VPC Management.
D. Configuration Management.
E. Data Center operations.
Answer
Correct answer: A, D

In order to implement best practices when dealing with a “Single Point of Failure,” you should attempt to build as much automation as possible in both detecting and reacting to failure. Which of the following AWS services would help? (Choose TWO)

A. ELB.
B. Auto Scaling.
C. Amazon Athen.
D. ECR.
E. Amazon EC2.
Answer
Correct answer: A, B

A company is planning to host an educational website on AWS. Their video courses will be streamed all around the world. Which of the following AWS services will help achieve high transfer speeds?

A. Amazon SNS.
B. Amazon Kinesis Video Streams.
C. AWS CloudFormation.
D. Amazon CloudFront.
Answer
Correct answer: D

A developer is planning to build a two-tier web application that has a MySQL database layer. Which of the following AWS database services would provide automated backups for the application?

A. A MySQL database installed on an EC2 instance.
B. Amazon Aurora.
C. Amazon DynamoDB.
D. Amazon Neptune.
Answer
Correct answer: B

What is the AWS service that enables AWS architects to manage infrastructure as code?

A. AWS CloudFormation.
B. AWS Config.
C. Amazon SES.
D. Amazon EMR.
Answer
Correct answer: A

Under the shared responsibility model, which of the following is the responsibility of AWS?

A. Client-side encryption.
B. Configuring infrastructure devices.
C. Server-side encryption.
D. Filtering traffic with Security Groups.
Answer
Correct answer: B

What does the AWS Health Dashboard provide? (Choose TWO)

A. Detailed troubleshooting guidance to address AWS events impacting your resources.
B. Health checks for Auto Scaling instances.
C. Recommendations for Cost Optimization.
D. A dashboard detailing vulnerabilities in your applications.
E. Personalized view of AWS service health.
Answer
Correct answer: A, E

You have deployed your application on multiple Amazon EC2 instances. Your customers complain that sometimes they can’t reach your application. Which AWS service allows you to monitor the performance of your EC2 instances to assist in troubleshooting these issues?

A. AWS Lambda.
B. AWS Config.
C. Amazon CloudWatch.
D. AWS CloudTrail.
Answer
Correct answer: C

Your company is developing a critical web application in AWS, and the security of the application is a top priority. Which of the following AWS services will provide infrastructure security optimization recommendations?

A. AWS Shield.
B. AWS Management Console.
C. AWS Secrets Manager.
D. AWS Trusted Advisor.
Answer
Correct answer: D

Which of the following is not a benefit of Amazon S3? (Choose TWO)

A. Amazon S3 provides unlimited storage for any type of data.
B. Amazon S3 can run any type of application or backend system.
C. Amazon S3 stores any number of objects, but with object size limits.
D. Amazon S3 can be scaled manually to store and retrieve any amount of data from anywhere.
E. Amazon S3 provides 99.999999999% (11 9’s) of data durability.
Answer
Correct answer: B, D

In the AWS Shared responsibility Model, which of the following are the responsibility of the customer? (Choose TWO)

A. Disk disposal.
B. Controlling physical access to compute resources.
C. Patching the Network infrastructure.
D. Setting password complexity rules.
E. Configuring network access rules.
Answer
Correct answer: D, E

What does AWS provide to deploy popular technologies such as IBM MQ on AWS with the least amount of effort and time?

A. Amazon Aurora.
B. Amazon CloudWatch.
C. AWS Quick Start reference deployments.
D. AWS OpsWorks.
Answer
Correct answer: C

An organization has decided to purchase an Amazon EC2 Reserved Instance (RI) for three years in order to reduce costs. It is possible that the application workloads could change during the reservation period. What is the EC2 Reserved Instance (RI) type that will allow the company to exchange the purchased reserved instance for another reserved instance with higher computing power if they need to?

A. Elastic RI.
B. Premium RI.
C. Standard RI.
D. Convertible RI.
Answer
Correct answer: D
```






    
    
    



