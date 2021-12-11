# NAT instance

![](/images/NAT-Instance-and-NAT-Gateway.jpeg)

* How can we have intenet in our private subnet and db instance to ping any website for and recieve a response
* AWS Nat Gateway - easy - Elastic IP
* AWS Nat Instance - logical Nat Instance - available in community/market place
* Bastion server or jump box - manual - another ec2 instance 18.04 config
## Task:
* Select AMI from AWS consel
* Choose the linux distro
* Launch it in our VPC within public subnet
* Enable public
* Disable/stop resource request check
![](/images/stop_nat_source_destination_check.png)

* Edit route table to allow 0.0.0.0 for nat instance
![](/images/rt_allow_nat_instance.png)

* Add some security rule in db security group
![](/images/db_sg_rules.png)

* copy eng99.pem file from local host to Nat instance
* SRP - Rsync - manually copy paste by creating a file with same name on nat instance

## Instructions
* Go to terminal `cd ~/.ssh` 
* Copy the key after this comand`Cat eng99.pem`
* SSH into NAT instance then `cd ~/.ssh`
* SSH into the db instance
* Create same key file name and past the key in here `sudo nano eng99.pem`
* Once you establshed the connection to db instance, ping a website such as `ping www.bbc.co.uk`

# Bastion Server Lab / Nat instance
![](/images/AWS_Bastion.png)
## Summary

Now that we've created a private subnet for our database instances we have a problem. We no longer have access to them via SSH.

To solve this we need to create a bastion server, also known as a jump box so that we can log in to the bastion and then from there access our database server to perform updates.

## Tasks

* Create a new public subnet called bastion
![](/images/bastion_subnet.png)

* Create a new ubuntu instance called bastion in this subnet
![](/images/Choose_AMI.png)

* Create a security group that only allows access on port 22 from your IP
![](/images/bastion_access_sg_only_22_myip.png)

* Create a security group called bastion-access that only allows ssh access from the bastion group
* SSH to your bastion server and from there SSH to your database instance
* `ping www.bbc.com` and get a response back



## What is Bastion host?
* Anything that provides perimeter access control security can be considered as the Bastion Host or Bastion Server. In fact, a Bastion host also known as a Jump Box is a particular purpose computer on a network that acts as a proxy server and allows the client machines to connect to the remote server. The Bastion hosts are used in cloud environments as a server to provide access to a private network from an external network such as the Internet. Since it is exposed to potential attack, a Bastion host must be protected against the chances of penetration.

* All your isolated instances have only internal IP addresses in your VPC. However, the Bastion host instance has an external IP address as well as an internal IP address. If you need to access instances on the internal network that do not have an external IP address, you can connect to a Bastion host and then connect to your internal instances from that Bastion host. This method uses a two-step SSH connection. Since the Bastion host uses a two-step SSH connection, it allows you to connect to the development environment without external IPs and additional firewall rules. When using a bastion host, you log into the bastion host first, and then into your target private instance. Because of this two-step login, the bastion hosts are sometimes called "jump servers."
The Bastion host can be started and stopped to enable or disable inbound SSH communication from the Internet.
## Instruction


* Launch it in our VPC within public subnet
![](/images/owned_vpc_enabled_publicip.png)

## You can use the following sequence of activities to use the SSH Agent forwarding from a Linux machine.

1. Make sure that your Public SSH Key is configured to both the Linux Bastion host and to the instancesthat do not have an external IP address. You can follow your Cloud provider’s document to get this configured.
2. Start the ssh-agent on your local machine. On most Linux systems, ssh-agent is automatically configured, and no additional actions are required to use it.
3. Use the ssh-add command to load your private SSH key from your local computer into the agent.
ssh-add <private-key-file> `ssh-add eng99.pem`
4. Connect to the Linux bastion host instance and forward your private keys with ssh. The -A argument sets the ForwardAgentoptions to yes and enablesprivate key forwarding. 
`ssh -A <user-name@bastion-host-external-ip>`
5. Connect to the instance that does not have an external IP address by using SSH.  
`ssh -A <user-name@internal-instance-internal-ip>`