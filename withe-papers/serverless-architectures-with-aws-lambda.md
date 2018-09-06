# Serverless Architectures with AWS Lambda

---

---

## Introduction -What Is Serverless?

---

No server management

Flexible scaling

High availability

No idle capacity

## AWS Lambda—the Basics

---

> _Lambda is a high-scale, provision-free serverless compute offering based on functions. It provides the cloud logic layer for your application_

![](/assets/serverless1.png)

## AWS Lambda—Diving Deeper

---

### Lambda Function Code

**The Function Code Package**

The function code package contains all of the assets you want to have available locally upon execution of your code

**The Handler**

The handler is a specific code method \(Java, C\#\) or function \(Node.js, Python\) that you’ve created and included in your package

**The Event Object**

When your Lambda function is invoked in one of the supported languages, one of the parameters provided to your handler function is an event object

**The Context Object**

{RequestId:'xxxx', RemainingTime:300, Logging:'CloudWatch Logs'}

**Writing Code for AWS Lambda—Statelessness and Reuse**

> _**your code cannotmake assumptions about state**_

![](/assets/lambdacode1.png)

### Lambda Function Event Sources

S3 event, SNS message, APIgateway call, Cloud Formation.......

**Invocation Patterns: Push Model&Pull Model**

**Push Model Event Sources:**

* Amazon S3
* Amazon API Gateway
* Amazon SNS
* AWS CloudFormation
* Amazon CloudWatch Events
* Amazon Alexa

**Pull Model Event Sources**

* Amazon DynamoDB
* Amazon Kinesis Streams

### Lambda Function Configuration

#### **Function Memory**

Not only will function memory dictate the amount of memory available to  
 your function code during execution, but the same dial will also influence the CPU and network resources available to your function.

#### **Versions and Aliases**

Amazon Resource Name \(ARN\):

> arn:aws:lambda:\[region\]:\[account\]:function:\[fn\_name\]:\[version\]

Each and every Lambda function has a default version built in: $LATEST

It’s important to know that a Lambda function container is specific to a particular version of your function

**Lambda aliases** should be used here, instead. A function alias allows you to invoke and point event sources to a specific Lambda function version.

Here are some example suggestions for Lambda aliases and how you might use them:

**• live/prod/active** – This could represent the Lambda function version that your production triggers or that clients are integrating with.

**• blue/green** – Enable the blue/green deployment pattern through use of aliases.

**• debug** – If you’ve created a testing stack to debug your applications, it can integrate with an alias like this when you need to perform a deeper analysis.

#### **IAM Role**



### Serverless Best Practices

---

### Serverless Architecture Best Practices

### Serverless Development Best Practices

## Sample Serverless Architectures

---

## Conclusion

---



