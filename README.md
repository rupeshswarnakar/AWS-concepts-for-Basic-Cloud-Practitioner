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
```






    
    
    



