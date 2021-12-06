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

# Step 1 - Create a VPC
# Step2 -  Internet Gateway(IG)
* 2.1 Attach the IG with our VPC
# Step3 - Public subnet for our app
# Step4- Create Route Table(RT) with routes/rules
* 4.1 Edit routes to allow IG and VPC
* 4.2 Associate our RT to our public subnet
# Create a security group now or create it at when we launch our app
* port 22 from my-ip
* port 3000
* port 80 HTTP
* HTTPS -SSL

# Create a private subnet in the same VPC
* Only allow app subnet to connect to DB subnet and instance
* Connect the app to the db
* Create SG for DB have these inbound rules:
  * Allow app ip. ie `10.0.1.0/24`
  * Allow port 22 - myIp for app instance
  * port `27017` for app ip
  * port `27017` from subnet ipv4/cdr block `10.0.1.0/24`
* Create NACL and allow app ip in inbound and outbound rules 

* `sudo nano .bashrc`
* `source ~/.bashrc`

## Setting up nginx as reverse proxy server
* - `sudo nano /etc/nginx/sites-available/default`
- Within the server block you should have an existing location / block. Replace the contents of that block with the following configuration. If your application is set to listen on a different port, update the highlighted portion to the correct port number.
 -     location / `{
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }`
* https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04
