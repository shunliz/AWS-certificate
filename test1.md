1, An IAM user is trying to perform an action on an object belonging to some other root account’s bucket. Which of the below mentioned options will AWS S3 not verify?

1. [ ] The object owner has provided access to the IAM user

2. [x] Permission provided by the parent of the IAM user on the bucket

3. [ ] Permission provided by the bucket owner to the IAM user

4. [ ] Permission provided by the parent of the IAM user

> If the IAM user is trying to perform some action on the object belonging to another AWS user’s bucket, S3 will verify whether the owner of the IAM user has given sufficient permission to him. It also verifies the policy for the bucket as well as the policy defined by the object owner.[http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-auth-workflow-object-operation.html](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-auth-workflow-object-operation.html)

2, Select the correct set of options. These are the initial settings for the default security group:

1. [ ] Allow all inbound traffic, Allow no outbound traffic and Allow instances associated with this security group to talk to each other.
2. [ ] Allow all inbound traffic, Allow all outbound traffic and Does NOT allow instances associated with this security group to talk to each other.
3. [x] Allow no inbound traffic, Allow all outbound traffic and Allow instances associated with this security group to talk to each other.
4. [ ] Allow no inbound traffic, Allow all outbound traffic and Does NOT allow instances associated with this security group to talk to each other.

> > Refer to [http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html\#default-security-group](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#default-security-group)



