# Practicing Continuous Integration and Continuous Delivery on AWS

---

---

## The Challenge of Software Delivery

operations stability and rapid feature  
 development

AWS now offers these CI/CD capabilities as a set of developer services: AWS  
 CodeStar,3 AWS CodeCommit,4 AWS CodePipeline,5 AWS CodeBuild,6 and  
 AWS CodeDeploy.7

---

## What is Continuous Integration and Continuous Delivery/Deployment?

---

### Continuous Integration

> _Continuous integration \(CI\) is a software development practice where  
>  developers regularly merge their code changes into a central repository, after  
>  which automated builds and tests are run_

### Continuous Delivery and Deployment

> _Continuous delivery \(CD\) is a software development practice where code  
>  changes are automatically built, tested, and prepared for production release_

### Continuous Delivery Is Not Continuous Deployment

> _One misconception about continuous delivery is that it means every change  
>  committed is applied to production immediately after passing automated tests_

## Benefits of Continuous Delivery

---

> _automating the process, improving developer productivity, improving code  
>  quality, and delivering updates to your customers faster_

Automate the Software Release Process

Improve Developer Productivity

Improve Code Quality

Deliver Updates Faster

## Implementing Continuous Integration and Continuous Delivery

---

### ![](/assets/cicd1.png)

### A Pathway to Continuous Integration/Continuous Delivery

![](/assets/cicd2.png)

### Teams![](/assets/cicd3.png)

### Testing Stages in Continuous Integration and Continuous Delivery

![](/assets/teststage.png)

**Unit Testing** – Tests a specific section of code to ensure the code does what it is expected to do. The unit testing is performed by software developers during the development phase. At this stage, a static code analysis, data flow analysis, code coverage, and other software verification processes can be applied.



**Integration Testing **– Verifies the interfaces between components against software design. Integration testing is an iterative process and facilitates building robust interfaces and system integrity.



**Component Testing **– Tests message passing between various components and their outcomes. A key goal of this testing could be idempotency in component testing. Tests can include extremely large data volumes, or edge situations and abnormal inputs.



**System Testing **– Tests the system end-to-end and verifies if the software satisfies the business requirement. This might include testing the UI, API, backend logic, and end state.



**Performance Testing** – Determines the responsiveness and stability of a system as it performs under a particular workload. Performance testing also is used to investigate, measure, validate, or verify other quality attributes of the system, such as scalability, reliability, and resource usage. Types of performance tests might include load tests, stress tests, and spike tests. Performance tests are used for benchmarking against predefined criteria.



**Compliance Testing** – Checks whether the code change complies with the requirements of a nonfunctional specification and/or regulations. It determines if you are implementing and meeting the defined standards.



**User Acceptance Testing** – Validates the end-to-end business flow. This testing is executed by an end user in a staging environment and confirms whether the system meets the requirements of the requirement specification. Typically, customers employ alpha and beta testing methodologies at this stage.



**Canary test** -- can be completed by deploying the new code only on a small subset of servers or even one server,

or one Region before deploying code to the entire production environment.



### Building the Pipeline

### Pipeline Integration with AWS CodeBuild

### Pipeline Integration with Jenkins

## Deployment Methods

---

### All at Once \(In-Place Deployment\)

### Rolling Deployment

### Immutable and Blue/Green Deployment

## Database Schema Changes

---

## Summary of Best Practices

---

## Conclusion

---

## Further Reading

---



