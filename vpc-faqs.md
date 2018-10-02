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
* **VPC Endpoints: **
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





