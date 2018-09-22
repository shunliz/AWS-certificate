**QUESTION 261**

You have a video transcoding application running on Amazon EC2. Each instance polls a queue to find out which video should be transcoded, and then runs a transcoding process. If this process is interrupted, the video will be transcoded by another instance based on the queuing system. You have a large backlog of videos which need to be transcoded and would like to reduce this backlog by adding more instances. You will need these instances only until the backlog is reduced. Which type of Amazon EC2 instances should you use to reduce the backlog in the most cost efficient way?

A. Reserved instances  
 B. Spot instances  
 C. Dedicated instances  
 D. On-demand instances

**Answer: B**

---

**QUESTION 262**

A customer has established an AWS Direct Connect connection to AWS. The link is up and routes are being advertised from the customer’s end, however the customer is unable to connect from EC2 instances inside its VPC to servers residing in its datacenter.  
Which of the following options provide a viable solution to remedy this situation? \(Choose 2 answers\)

A. Add a route to the route table with an iPsec VPN connection as the target.

B. Enable route propagation to the virtual pinnate gateway \(VGW\).

C. Enable route propagation to the customer gateway \(CGW\).

D. Modify the route table of all Instances using the ‘route’ command.

E. Modify the Instances VPC subnet route table by adding a route back to the customer’s on-premises environment.

**Answer: B,E**

---



