Q**uestion 1**

REST or Query requests are HTTP or HTTPS requests that use an HTTP verb \(such as GET or POST\) and a parameter named Action or Operation that specifies the API you are calling.

1. FALSE
2. **TRUE**

Q**uestion 2**

Through which of the following interfaces is AWS Identity and Access Management available?

A\) AWS Management Console

B\) Command line interface \(CLI\)

C\) IAM Query API

D\) Existing libraries

1. Only through Command line interface \(CLI\)
2. A, B and C
3. A and C
4. **All of the above**

Q**uestion 3**

Which of the following programming languages have an officially supported AWS SDK? Choose 2 answers

1. **PHP**
2. Pascal
3. **Java**
4. SQL
5. Perl

Q**uestion 4**

HTTP Query-based requests are HTTP requests that use the HTTP verb GET or POST and a Query parameter named\_\_\_\_\_\_\_\_\_\_\_\_\_.

1. **Action**
2. Value
3. Reset
4. Retrieve

Q**uestion 5**

An AWS customer is deploying an application that is composed of an AutoScaling group of EC2 Instances. The customers security policy requires that every outbound connection from these instances to any other service within the customers Virtual Private Cloud must be authenticated using a unique x.509 certificate that contains the specific instanceid. In addition an x.509 certificates must be designed by the customer’s Key management service in order to be trusted for authentication. Which of the following configurations will support these requirements?

1. Configure an IAM Role that grants access to an Amazon S3 object containing a signed certificate and configure the Auto Scaling group to launch instances with this role. Have the instances bootstrap get the certificate from Amazon S3 upon first boot.
2. Embed a certificate into the Amazon Machine Image that is used by the Auto Scaling group. Have the launched instances generate a certificate signature request with the instance’s assigned instance-id to the Key management service for signature.
3. **Configure the Auto Scaling group to send an SNS notification of the launch of a new instance to the trusted key management service. Have the Key management service generate a signed certificate and send it directly to the newly launched instance.**
4. Configure the launched instances to generate a new certificate upon first boot. Have the Key management service poll the AutoScaling group for associated instances and send new instances a certificate signature that contains the specific instance-id.

Q**uestion 6**

When assessing an organization AWS use of AWS API access credentials which of the following three credentials should be evaluated? Choose 3 answers

1. Key pairs
2. **Console passwords**
3. **Access keys**
4. **Signing certificates**
5. Security Group memberships \(required for EC2 instance access\)



