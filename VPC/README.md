### AWS VPC
# What is CIDR block?
* A virtual private cloud (VPC) is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC.

When you create a VPC, you must specify a range of IPv4 addresses for the VPC in the form of a Classless Inter-Domain Routing (CIDR) block; for example, 10.0.0.0/16. This is the primary CIDR block for your VPC.

# What is an IPve 4 and IPve6?
* Subnet types
When you create a subnet, depending on the configurations set for the VPC and the configurations you set for the subnet, you have the following IPv4 and IPv6 options:

  * IPv4-only: Your VPC is associated with an IPv4 CIDR or both IPv4 and IPv6 CIDRs. If the subnet CIDRs you choose are IPv4 CIDR ranges, any EC2 instances launched within the subnet will communicate over IPv4-only.

  * Dual-stack (IPv4 and IPv6): Your VPC is associated with an IPv4 CIDR or both IPv4 and IPv6 CIDRs. As a result, any subnets you create in the VPC can be dual-stack subnets. Any EC2 instances launched within the subnet will communicate over the IP of the subnet.

  * IPv6-only: Your VPC is associated with both IPv4 and IPv6 CIDRs. If you select the IPv6-only option when you create the subnet, any EC2 instances launched within the subnet will communicate over IPv6-only.
# What is route table (RT)?
* Your VPC has an implicit router, and you use route tables to control where network traffic is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for the subnet (subnet route table). You can explicitly associate a subnet with a particular route table. Otherwise, the subnet is implicitly associated with the main route table. A subnet can only be associated with one route table at a time, but you can associate multiple subnets with the same subnet route table.
# What is an internet Gateway(IG)?
* An internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.

An internet gateway serves two purposes: to provide a target in your VPC route tables for internet-routable traffic, and to perform network address translation (NAT) for instances that have been assigned public IPv4 addresses.
# VPC and subnet Range
* IP Subnet range: 
A subnetwork or subnet is a logical subdivision of an IP network. The practice of dividing a network into two or more networks is called subnetting. ... Addresses in the range 198.51.100.0 to 198.51.100.255 belong to this network, with 198.51.100.255 as the subnet broadcast address.
# What is NACLs?
* A network access control list (ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. You might set up network ACLs with rules similar to your security groups in order to add an additional layer of security to your VPC.
# What is the different between stateless and statefull (NACL vs SG)?
* Security groups are stateful: This means any changes applied to an incoming rule will be automatically applied to the outgoing rule. e.g. If you allow an incoming port 80, the outgoing port 80 will be automatically opened.
Network ACLs are stateless: This means any changes applied to an incoming rule will not be applied to the outgoing rule. e.g. If you allow an incoming port 80, you would also need to apply the rule for outgoing traffic.
