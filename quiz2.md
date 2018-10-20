**Questions 1**

You are designing a personal document-archiving solution for your global enterprise with thousands of employee. Each employee has potentially gigabytes of data to be backed up in this archiving solution. The solution will be exposed to he employees as an application, where they can just drag and drop their files to the archiving system. Employees can retrieve their archives through a web interface. The corporate network has high bandwidth AWS DirectConnect connectivity to AWS. You have regulatory requirements that all data needs to be encrypted before being uploaded to the cloud. How do you implement this in a highly available and cost efficient way?

1. Manage encryption keys on-premise in an encrypted relational database. Set up an on-premises server with sufficient storage to temporarily store files and then upload them to Amazon S3, providing a client-side master key. \(Storing temporary increases cost and not a high availability option\)
2. Manage encryption keys in a Hardware Security Module\(HSM\) appliance on-premise server with sufficient storage to temporarily store, encrypt, and upload files directly into amazon Glacier. \(Not cost effective\)
3. **Manage encryption keys in amazon Key Management Service \(KMS\), upload to amazon simple storage service \(s3\) with client-side encryption using a KMS customer master key ID and configure Amazon S3 lifecycle policies to store each object using the amazon glacier storage tier.**
   \(with CSE-KMS the encryption happens at client side before the object is upload to S3 and KMS is cost effective as well\)
4. Manage encryption keys in an AWS CloudHSM appliance. Encrypt files prior to uploading on the employee desktop and then upload directly into amazon glacier \(Not cost effective\)







