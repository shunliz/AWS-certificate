**Q. What is Amazon Virtual Private Cloud?**

Amazon VPC lets you provision a logically isolated section of the Amazon Web Services \(AWS\) cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including selection of your own IP address ranges, creation of subnets, and configuration of route tables and network gateways. You can also create a hardware Virtual Private Network \(VPN\) connection between your corporate datacenter and your VPC and leverage the AWS cloud as an extension of your corporate datacenter.

You can easily customize the network configuration for your Amazon VPC. For example, you can create a public-facing subnet for your web servers that have access to the Internet, and place your backend systems such as databases or application servers in a private-facing subnet with no Internet access. You can leverage multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet.

**Q. What are the components of Amazon VPC?**

Amazon VPC comprises a variety of objects that will be familiar to customers with existing networks:

* **A Virtual Private Cloud:**
  A logically isolated virtual network in the AWS cloud. You define a VPC’s IP address space from ranges you select.
* **Subnet:**
  A segment of a VPC’s IP address range where you can place groups of isolated resources.
* **Internet Gateway:**
  The Amazon VPC side of a connection to the public Internet.
* **NAT Gateway:**
  A highly available, managed Network Address Translation \(NAT\) service for your resources in a private subnet to access the Internet.
* **Hardware VPN Connection:**
  A hardware-based VPN connection between your Amazon VPC and your datacenter, home network, or co-location facility.
* **Virtual Private Gateway:**
  The Amazon VPC side of a VPN connection.
* **Customer Gateway:**
  Your side of a VPN connection.
* **Peering Connection:**
  A peering connection enables you to route traffic via private IP addresses between two peered VPCs.
* **VPC Endpoints: **
  Enables private connectivity to services hosted in AWS, from within your VPC without using an Internet Gateway, VPN, Network Address Translation \(NAT\) devices, or firewall proxies.
* **Egress-only Internet Gateway:**
  A stateful gateway to provide egress only access for IPv6 traffic from the VPC to the Internet.

、

**Q. What are the different types of VPC Endpoints available on Amazon VPC?**

VPC endpoints enable you to privately connect your VPC to services hosted on AWS without requiring an Internet gateway, a NAT device, VPN, or firewall proxies. Endpoints are horizontally scalable and highly available virtual devices that allow communication between instances in your VPC and AWS services. Amazon VPC offers two different types of endpoints: gateway type endpoints and interface type endpoints.

Gateway type endpoints are available only for AWS services including S3 and DynamoDB. These endpoints will add an entry to your route table you selected and route the traffic to the supported services through Amazon’s private network.

Interface type endpoints provide private connectivity to services powered by PrivateLink, being AWS services, your own services or SaaS solutions, and supports connectivity over Direct Connect. More AWS and SaaS solutions will be supported by these endpoints in the future. Please refer to VPC Pricing for the price of interface type endpoints.

**Q. What are the connectivity options for my VPC?**

You may connect your VPC to:

* The Internet \(via an Internet gateway\)
* Your corporate data center using a Hardware VPN connection \(via the virtual private gateway\)
* Both the Internet and your corporate data center \(utilizing both an Internet gateway and a virtual private gateway\)
* Other AWS services \(via Internet gateway, NAT, virtual private gateway, or VPC endpoints\)
* Other VPCs \(via VPC peering connections\)

**Q. How do I connect my VPC to the Internet?**

Amazon VPC supports the creation of an Internet gateway. This gateway enables Amazon EC2 instances in the VPC to directly access the Internet.

**Q. How do instances in a VPC access the Internet?**

You can use public IP addresses, including Elastic IP addresses \(EIPs\), to give instances in the VPC the ability to both directly communicate outbound to the Internet and to receive unsolicited inbound traffic from the Internet \(e.g., web servers\). You can also use the solutions in the next question.

**Q. How do instances without public IP addresses access the Internet**

Instances without public IP addresses can access the Internet in one of two ways:

1. Instances without public IP addresses can route their traffic through a NAT gateway or a NAT instance to access the Internet. These instances use the public IP address of the NAT gateway or NAT instance to traverse the Internet. The NAT gateway or NAT instance allows outbound communication but doesn’t allow machines on the Internet to initiate a connection to the privately addressed instances.
2. For VPCs with a hardware VPN connection or Direct Connect connection, instances can route their Internet traffic down the virtual private gateway to your existing datacenter. From there, it can access the Internet via your existing egress points and network security/monitoring devices.

**Q. Can I connect to my VPC using a software VPN?**

Yes. You may use a third-party software VPN to create a site to site or remote access VPN connection with your VPC via the Internet gateway.

**Q. How does a hardware VPN connection work with Amazon VPC?**

A hardware VPN connection connects your VPC to your datacenter. Amazon supports Internet Protocol security \(IPsec\) VPN connections. Data transferred between your VPC and datacenter routes over an encrypted VPN connection to help maintain the confidentiality and integrity of data in transit. An Internet gateway is not required to establish a hardware VPN connection.

**Q. What is IPsec?**

[IPsec](http://en.wikipedia.org/wiki/IPsec) is a protocol suite for securing Internet Protocol \(IP\) communications by authenticating and encrypting each IP packet of a data stream.

**Q. Which customer gateway devices can I use to connect to Amazon VPC**

There are two types of VPN connections that you can create: statically-routed VPN connections and dynamically-routed VPN connections. Customer gateway devices supporting statically-routed VPN connections must be able to:

* Establish IKE Security Association using Pre-Shared Keys
* Establish IPsec Security Associations in Tunnel mode
* Utilize the AES 128-bit or 256-bit encryption function
* Utilize the SHA-1 or SHA-2 \(256\) hashing function
* Utilize Diffie-Hellman \(DH\) Perfect Forward Secrecy in "Group 2" mode, or one of the additional DH groups we support
* Perform packet fragmentation prior to encryption

In addition to the above capabilities, devices supporting dynamically-routed VPN connections must be able to:

* Establish Border Gateway Protocol \(BGP\) peerings
* Bind tunnels to logical interfaces \(route-based VPN\)
* Utilize IPsec Dead Peer Detection

**Q. What is the approximate maximum throughput of a VPN connection?**

VGW supports IPSEC VPN throughput upto 1.25 Gbps. Multiple VPN connections to the same VPC are cumulatively bound by the VGW throughput of 1.25 Gbps.

**Q. What factors affect the throughput of my VPN connection?**

VPN connection throughput can depend on multiple factors, such as the capability of your Customer Gateway \(CGW\), the capacity of your connection, average packet size, the protocol being used \(TCP vs. UDP\), and the network latency between your CGW and the Virtual Private Gateway \(VGW\).

**Q. What tools are available to me to help troubleshoot my Hardware VPN configuration?**

The DescribeVPNConnection API displays the status of the VPN connection, including the state \("up"/"down"\) of each VPN tunnel and corresponding error messages if either tunnel is "down". This information is also displayed in the AWS Management Console.

**Q. How do I connect a VPC to my corporate datacenter?**

Establishing a hardware VPN connection between your existing network and Amazon VPC allows you to interact with Amazon EC2 instances within a VPC as if they were within your existing network. AWS does not perform

[network address translation \(NAT\)](http://en.wikipedia.org/wiki/Network_address_translation)

on Amazon EC2 instances within a VPC accessed via a hardware VPN connection.

**Q. Can I NAT my CGW behind a router or firewall?**

Yes, you will need to enable NAT-T and open UDP port 4500 on your NAT device.

**Q. What IP address do I use for my CGW address?**

You will use the public IP address of your NAT device.

**Q: How many IPsec security associations can be established concurrently per tunnel?**

The AWS VPN service is a route-based solution, so when using a route-based configuration you will not run into SA limitations. If, however, you are using a policy-based solution you will need to limit to a single SA, as the service is a route-based solution.

**Q. How do I assign IP address ranges to VPCs?**

You assign a single[Classless Internet Domain Routing \(CIDR\)](http://en.wikipedia.org/wiki/CIDR)IP address range as the primary CIDR block when you create a VPC and can add up to four \(4\) secondary CIDR blocks after creation of the VPC. Subnets within a VPC are addressed from these CIDR ranges by you. Please note that while you can create multiple VPCs with overlapping IP address ranges, doing so will prohibit you from connecting these VPCs to a common home network via the hardware VPN connection. For this reason we recommend using non-overlapping IP address ranges. You can allocate an Amazon-provided IPv6 CIDR block to your VPC.

**Q. What IP address ranges are assigned to a default VPC?**

Default VPCs are assigned a CIDR range of 172.31.0.0/16. Default subnets within a default VPC are assigned /20 netblocks within the VPC CIDR range.

**Q. Can I use my public IPv4 addresses in VPC and access them over the Internet?**

Yes, you can bring your public IPv4 addresses into AWS VPC and statically allocate them to subnets and EC2 instances. To access these addresses over the Internet, you will have to advertise them to the Internet from your on-premises network. You will also have to route the traffic over these addresses between your VPC and on-premises network using AWS DX or AWS VPN connection. You can route the traffic from your VPC using the Virtual Private Gateway. Similarly, you can route the traffic from your on-premises network back to your VPC using your routers.

**Q. How large of a VPC can I create?**

Currently, Amazon VPC supports five \(5\) IP address ranges, one \(1\) primary and four \(4\) secondary for IPv4. Each of these ranges can be between /28 \(in CIDR notation\) and /16 in size. The IP address ranges of your VPC should not overlap with the IP address ranges of your existing network.

For IPv6, the VPC is a fixed size of /56 \(in CIDR notation\). A VPC can have both IPv4 and IPv6 CIDR blocks associated to it.

**Q. Can I change the size of a VPC?**

Yes. You can expand your existing VPC by adding four \(4\) secondary IPv4 IP ranges \(CIDRs\) to your VPC. You can shrink your VPC by deleting the secondary CIDR blocks you have added to your VPC. You cannot however change the size of the IPv6 address range of your VPC.

**Q. How many subnets can I create per VPC?**

Currently you can create 200 subnets per VPC. If you would like to create more, please[submit a case at the support center](https://amazonaws-china.com/contact-us/vpc-request/).

**Q. Is there a limit on how large or small a subnet can be?**

The minimum size of a subnet is a /28 \(or 14 IP addresses.\) for IPv4. Subnets cannot be larger than the VPC in which they are created.

For IPv6, the subnet size is fixed to be a /64. Only one IPv6 CIDR block can be allocated to a subnet.

**Q. Can I change the private IP addresses of an Amazon EC2 instance while it is running and/or stopped within a VPC?**

Primary private IP addresses are retained for the instance's or interface's lifetime. Secondary private IP addresses can be assigned, unassigned, or moved between interfaces or instances at any time.

**Q. If an Amazon EC2 instance is stopped within a VPC, can I launch another instance with the same IP address in the same VPC?**

No. An IP address assigned to a running instance can only be used again by another instance once that original running instance is in a “terminated” state.





**Q. Can I assign any IP address to an instance?**

You can assign any IP address to your instance as long as it is:

* Part of the associated subnet's IP address range
* Not reserved by Amazon for IP networking purposes
* Not currently assigned to another interface

**Q. Can I assign one or more Elastic IP \(EIP\) addresses to VPC-based Amazon EC2 instances?**

Yes, however, the EIP addresses will only be reachable from the Internet \(not over the VPN connection\). Each EIP address must be associated with a unique private IP address on the instance. EIP addresses should only be used on instances in subnets configured to route their traffic directly to the Internet gateway. EIPs cannot be used on instances in subnets configured to use a NAT gateway or a NAT instance to access the Internet. This is applicable only for IPv4. Amazon VPCs do not support EIPs for IPv6 at this time.

**Q. Can I specify which subnet will use which gateway as its default?**

Yes. You may create a default route for each subnet. The default route can direct traffic to egress the VPC via the Internet gateway, the virtual private gateway, or the NAT gateway.

**Q. Does Amazon VPC support**[**multicast**](http://en.wikipedia.org/wiki/IP_multicast)**or**[**broadcast**](http://en.wikipedia.org/wiki/Broadcast_address#IP_network_broadcasting)**?**

No.



