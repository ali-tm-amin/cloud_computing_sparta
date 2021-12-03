## Amazon Web Services
### EC2
* Create an EC2 instance -VM
* Ubuntu 18.04LTS
* Determine the size of VM
* Establish a security group
* SSH into the machine 
* `cd ~/.ssh` copy and past SSH compands from aws counsel/client connect
* cd into app folder
* Update and Upgrade `sudo apt-get update -y` `sudo apt-get upgrade -y`
* Install NGINX `sudo apt-get install nginx -y`
  * Will be available publicly
* npm start
* Require a public ip for the EC2 Instance
* transfer the app via securecp `scp` or rsync
install dependencies

### UsingSynce:
rsync -avzh -e "ssh -i eng99.pem" /Vagrant/starter-code/app/ ubuntu@ec2-34-245-24-17.eu-west  
-1.compute.amazonaws.com:/home/ubuntu/app
* scp -i pem_file file_to_copy user@ip:/destination
example: `scp -i "~/.ssh/eng99.pem" restaurant.py ubuntu@e***.com:/home/ubuntu/new_folder/restaurant.py`
# cloud_computing_sparta
## What is cloud computing 
Cloud computing is the on-demand availability of computer system resources, especially data storage and computing power, without direct active management by the user. Large clouds often have functions distributed over multiple locations, each location being a data center.

## What are the benefits?
* Reduced IT costs. Moving to cloud computing may reduce the cost of managing and maintaining your IT systems. ...
* Scalability. ...
* Business continuity. ...
* Collaboration efficiency. ...
* Flexibility of work practices. ...
* Access to automatic updates. ...

## Who is using it in IT tech
* Organizations of every type, size and industry use the cloud for varying use cases such as data backup, disaster recovery, email, virtual desktops, software development and testing, big data analytics, and customer-facing web applications.

* E.g. Healthcare companies are using the cloud to develop more personalized treatments for patients. Financial services companies are using the cloud to power real time fraud detection and prevention. And video game makeers are using the cloud to deliver online games to millions of players around the world.

* Sooner or later every organisaion start adapting could services.

## Types of Cloud Computing

### Infrastructure as a Service (IaaS) 
Contains the basic building blocks for cloud IT. Provides access to networking features, computers and data storage space. IaaS delivers the highest level of flxibility and management control over your IT resources.

### Platform as a Service (PaaS) 
Removes the need for you to manage underlying infrastructure (hardware and OS), and allows you to focus on the deployment and management of your applications. This helps you be more efficient as you dont need to worry about resource procurement, capacity planning, software maintenance, patching or any of the other undifferentiated heavy lifting involved in running your application.

### Software as a Service (SaaS) 
Provides you with a complete product that is run and managed by the service provider. You dont have to think about how the service is maintained or how the underlying infrastructure is managed. You only need to think about how you will use that particular software.

## What is AWS? 
Amazon Web Service is the world's most comprehensive and broadly adopted cloud platform, offering over 200 fully featured services from data centers globally. Millions of customers - including the fastest growing startups, largest enterprises and leading government agencies are using AWS to lower costs, become more agile and innovate faster.

## Benefits of AWS

Most Functionality
Largest Community of Customers and Partners
Most Secure
Fastest Pace of Innovation
Most Proven Operational Expertise
Global Network of AWS Regions with Availability Zones