# Blue/Green Deployments on AWS

---

---

## Introduction

---

### Blue/Green Deployment Methodology

The fundamental idea behind blue/green deployment is to shift traffic between two identical environments that are running different versions of your application

### Benefits of Blue/Green

simply roll traffic back to the still-operating blue environment is a key benefit of blue/green deployments

Blue/green deployments also fit well with continuous integration and continuous deployment \(CI/CD\) workflows, in many cases limiting their complexity.

blue/green deployments also provide cost optimization benefits

### Define the Environment Boundary

where have things changed and what needs to be deployed to make those changes live.

## AWS Tools and Services Enabling Blue/Green Deployments

---

### Amazon Route 53

### Elastic Load Balancing

### Auto Scaling

### AWS Elastic Beanstalk

### AWS OpsWorks

### AWS CloudFormation

### Amazon CloudWatch

## Techniques

---

### Update DNS Routing with Amazon Route 53

### Swap the Auto Scaling Group Behind Elastic Load Balancer

### Update Auto Scaling Group Launch Configurations

### Swap the Environment of an Elastic Beanstalk Application

### Clone a Stack in AWS OpsWorks and Update DNS

## Best Practices for Managing Data Synchronization and Schema Changes

---

### Decoupling Schema Changes from Code Changes

### When Blue/Green Deployments Are Not Recommended

## Conclusion

---



