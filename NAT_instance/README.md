# NAT instance

![](/NAT-Instance-and-NAT-Gateway.jpeg)

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
![](/stop_nat_source_destination_check.png)
* Edit route table to allow 0.0.0.0 for nat instance
![](/rt_allow_nat_instance.png)
* Add some security rule in db security group
![](/db_sg_rules.png)
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
![](/AWS_Bastion.png)
## Summary

Now that we've created a private subnet for our database instances we have a problem. We no longer have access to them via SSH.

To solve this we need to create a bastion server, also known as a jump box so that we can log in to the bastion and then from there access our database server to perform updates.

## Tasks

* Create a new public subnet called bastion
* Create a new ubuntu instance called bastion in this subnet
* Create a security group that only allows access on port 22 from your IP
* Create a security group called bastion-access that only allows ssh access from the bastion group
* SSH to your bastion server and from there SSH to your database instance
* `ping www.bbc.com` and get a response back

## Instruction
* Go to AWS Consol
* Create bastion subnet
![](/bastion_subnet.png)
* Choose the linux NAT
![](/Choose_AMI.png)
* Launch it in our VPC within public subnet
![](/owned_vpc_enabled_publicip.png)
* Create a security group that only allows access on port 22 from your IP
![](/bastion_access_sg_only_22_myip.png)
* Disable/stop resource request check
* Edit route table to allow 0.0.0.0 for nat instance
* Add some security rule in db security group
* copy eng99.pem file from local host to Nat instance
* SRP - Rsync - manually copy paste by creating a file with same name on nat instance
