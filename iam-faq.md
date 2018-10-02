**Q: How do I get started with IAM?**

To start using IAM, you must subscribe to at least one of the AWS services that is integrated with IAM. You then can create and manage users, groups, and permissions via IAM APIs, the AWS CLI, or the IAM console, which gives you a point-and-click, web-based interface. You can also use the visual editor to create policies.

**Q: How are IAM users managed?**  
IAM supports multiple methods to:

* Create and manage IAM users.
* Create and manage IAM groups.
* Manage users' security credentials.
* Create and manage policies to grant access to AWS services and resources.

You can create and manage users, groups, and policies by using IAM APIs, the [AWS CLI](http://aws.amazon.com/cli/), or the[IAM console](https://console.aws.amazon.com/iam/home). You also can use the[visual editor](https://docs.aws.amazon.com/console/iam/create-policies)and the [IAM policy simulator](https://policysim.aws.amazon.com/)to create and test policies.

**Q: What kinds of security credentials can IAM users have?**

IAM users can have any combination of credentials that AWS supports, such as an AWS access key, X.509 certificate, SSH key, password for web app logins, or an[MFA](https://amazonaws-china.com/identity/saml/)device. This allows users to interact with AWS in any manner that makes sense for them. An employee might have both an AWS access key and a password; a software system might have only an AWS access key to make programmatic calls; IAM users might have a private SSH key to access AWS CodeCommit repositories; and an outside contractor might have only an X.509 certificate to use the EC2 command-line interface. For details, see [Temporary Security Credentials](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingLogins.html) in the IAM documentation.

**Q: Where can I use my SSH keys?**

Currently, IAM users can use their SSH keys only with AWS CodeCommit to access their repositories.

**Q: How are user passwords set?**

You can set an initial password for an IAM user via the [IAM console](https://console.aws.amazon.com/iam/home) [AWS CLI](http://amazonaws-china.com/cli/), or IAM APIs. User passwords never appear in clear text after the initial provisioning, and are never displayed or returned via an API call. IAM users can manage their passwords via the **My Password **page in the IAM console. Users access this page by selecting the **Security Credentials **option from the drop-down list in the upper right corner of the AWS Management Console.

**Q: Can I define a password policy for my user’s passwords?**

Yes, you can enforce strong passwords by requiring minimum length or at least one number. You can also enforce automatic password expiration, prevent re-use of old passwords, and require a password reset upon the next AWS sign-in.

**Q: What is an IAM role?**

  


An IAM role is an IAM entity that defines a set of [permissions](https://amazonaws-china.com/iam/details/manage-permissions/) for making AWS service requests. IAM roles are not associated with a specific user or group. Instead, trusted entities assumeroles, such as IAM users, applications, or AWS services such as EC2.



**Q: How many IAM roles can I assume?**

  


There is no limit to the number of IAM roles you can assume, but you can only act as one IAM role when making requests to AWS services.



**Q: How many policies can I attach to an IAM role?**

**For**[**inline policies**](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html)**:**You can add as many inline policies as you want to a user, role, or group, but the total aggregate policy size \(the sum size of all inline policies\) per entity cannot exceed the following limits:

* User policy size cannot exceed 2,048 characters.
* Role policy size cannot exceed 10,240 characters.
* Group policy size cannot exceed 5,120 characters.



**Q: How many IAM roles can I create?**

  


You are limited to 1,000 IAM roles under your AWS account. If you need more roles, submit the

[IAM limit increase request form](https://portal.aws.amazon.com/gp/aws/html-forms-controller/iam-limit-increase-request)

with your use case, and we will consider your request.

**Q: What are the features of IAM roles for EC2 instances?**  


IAM roles for EC2 instances provides the following features:

* AWS temporary security credentials to use when making requests from running EC2 instances to AWS services.
* Automatic rotation of the AWS temporary security credentials.
* Granular AWS service permissions for applications running on EC2 instances.



