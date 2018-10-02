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

  


IAM users can have any combination of credentials that AWS supports, such as an AWS access key, X.509 certificate, SSH key, password for web app logins, or an

[MFA](https://amazonaws-china.com/identity/saml/)

device. This allows users to interact with AWS in any manner that makes sense for them. An employee might have both an AWS access key and a password; a software system might have only an AWS access key to make programmatic calls; IAM users might have a private SSH key to access AWS CodeCommit repositories; and an outside contractor might have only an X.509 certificate to use the EC2 command-line interface. For details, see

[Temporary Security Credentials](http://docs.aws.amazon.com/IAM/latest/UserGuide/Using_ManagingLogins.html)

in the IAM documentation.

