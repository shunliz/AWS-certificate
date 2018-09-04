# Microservices on AWS

## Introduction

---

### Characteristics of Microservices

Decentralized

Independent

Do one thing well

Polyglot

Black box

You build it; you run it

![](/assets/devops1.png)

### Benefits of Microservices

Agility

Innovation

Quality

Scalability

Availability

### Challenges of Microservices

**problems**

Distributed Systems

Migration

Versions

Organization

**Architectural Complexity**

![](/assets/microservicecomplex1.png)**Operational Complexity**

..................................

### Microservices and the Cloud

On-demand resources

Experiment with low cost and risk

Programmability

Infrastructure as code

Continuous Delivery

Managed services

Service orientation

Polyglot

## Microservices on AWS

---

### Simple Microservices Architecture on AWS

![](/assets/simplemicroservice.png)

### Reducing Operational Complexity

API Implementation

> _API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale._

![](/assets/apigateway1.png)

> _AWS Lambda lets you run code without provisioning or managing servers.27 You pay only for the compute time you consume – there is no charge when your code is not running. With Lambda, you can run code for virtually any type of application or backend service – all with zero administration_

### Distributed Systems Components

#### Service Discovery

**Client-Side Service Discovery**

> _hardcode the IP address of the target as part of the configuration of the  
> communication source_

**Application Load Balancer-Based Service Discovery    
**

> > _One of the advantages of Application Load Balancing is that it provides health checks and automatic registration/de-registration of backend services in failure cases. The Application Load Balancer also offers path- and host-based routing approaches. Combining these features with DNS capabilities, it’s possible to build a simple service discovery solution with minimum efforts and low cost_

**DNS-Based Service Discovery**

![](/assets/route53.png)

**Service Discovery Using Amazon ECS Event Stream**

![](/assets/svdesc1.png)**Service Discovery Using Configuration Management**

> _OpsWorks is a configuration management service that uses Chef, an automation platform that treats server configurations as code. OpsWorks uses Chef to automate how servers are configured, deployed, and managed across your EC2 instances or on-premises compute environments._

![](/assets/svcdesc2.png)**Service Discovery Using Key Value Store**

![](/assets/svcdesc3.png)

**Third-party software**

HashiCorp Consul, etcd, or Netflix Eureka

#### Distributed Data Management

**event sourcing **

> _The core idea behind event sourcing is to represent and persist every application change as an    
> _
>
> _event record. Instead of persisting application state, data is stored as a stream of events_
>
> _Kinesis Streams enables you to build custom applications that process or analyze streaming data for specialized needs.48 Kinesis Streams can continuously capture and store terabytes of data per hour from hundreds of thousands of sources, such as website clickstreams, financial transactions, social media feeds, IT logs, and location-tracking events._

![](/assets/eventsource1.png)**CQRS**

![](/assets/cqrs1.png)

#### Asynchronous Communication and Lightweight Messaging



## Conclusion

---



