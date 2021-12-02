### Step by step guide for creating AWS service
## EC2:
* Amazon Elastic Compute Cloud (EC2) is a part of Amazon.com's cloud-computing platform, Amazon Web Services (AWS), that allows users to rent virtual computers on which to run their own computer applications. EC2 encourages scalable deployment of applications by providing a web service through which a user can boot an Amazon Machine Image (AMI) to configure a virtual machine, which Amazon calls an "instance", containing any software desired. A user can create, launch, and terminate server-instances as needed, paying by the second for active servers – hence the term "elastic". EC2 provides users with control over the geographical location of instances that allows for latency optimization and high levels of redundancy. In November 2010, Amazon switched its own retail website platform to EC2 and AWS.

## SG:
* An AWS security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Both inbound and outbound rules control the flow of traffic to and traffic from your instance, respectively.

## AMI:
* An Amazon Machine Image (AMI) provides the information required to launch an instance. ... Launch permissions that control which AWS accounts can use the AMI to launch instances. A block device mapping that specifies the volumes to attach to the instance when it's launched.

## Cloud watch: 
* Amazon CloudWatch is a monitoring and management service that provides data and actionable insights for AWS, hybrid, and on-premises applications and infrastructure resources. ... You can use CloudWatch Container Insights to monitor, troubleshoot, and alert your containerized applications and microservices

## Alarms:
* Alarms watch metrics and execute actions by publishing notifications to Amazon SNS topics or by initiating Auto Scaling actions. SNS can deliver notifications using HTTP, HTTPS, Email, or an Amazon SQS queue. Your application can receive these notifications and then act on them in any desired way.

## SNS 
* Amazon Simple Notification Service (Amazon SNS) is a fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

* The A2A pub/sub functionality provides topics for high-throughput, push-based, many-to-many messaging between distributed systems, microservices, and event-driven serverless applications. Using Amazon SNS topics, your publisher systems can fanout messages to a large number of subscriber systems, including Amazon SQS queues, AWS Lambda functions, HTTPS endpoints, and Amazon Kinesis Data Firehose, for parallel processing. The A2P functionality enables you to send messages to users at scale via SMS, mobile push, and email.

## Making EC2 app highly available:
there are several possibilities to achieve HA with EC2:
* create an autoscaling group with min capacity=1 and max capacity=1. So whenever your instance fails, the autoscaling group will create a new one. The autoscaling group comes for free, so this is not a bad solution depending on your SLA.
* use ec2 auto-recovery feature by creating a cloudwatch alarm that would replace your instance if failed.
* create two EC2 instances and use Route 53 DNS failover to resolve to an healthy instance
* Last but not least: the best solution is definitely to create several instances across several availability zones and to use an elastic load balancer to distribute the traffic. This way, even if an instance fails, you already have other ones available. AWS recommends this solution as they have an SLA of 99.95% for their instance in an AZ. By putting in several AZs you can have 100% availability

## Making EC2 highly scalable with Auto Scaling:
* Amazon EC2 Auto Scaling helps you ensure that you have the correct number of Amazon EC2 instances available to handle the load for your application. You create collections of EC2 instances, called Auto Scaling groups. You can specify the minimum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes below this size. You can specify the maximum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling ensures that your group never goes above this size. If you specify the desired capacity, either when you create the group or at any time thereafter, Amazon EC2 Auto Scaling ensures that your group has this many instances. If you specify scaling policies, then Amazon EC2 Auto Scaling can launch or terminate instances as demand on your application increases or decreases.

## Services required to make EC2 highly Availabe & Scalable:
* At last 2 availability zone
* Elastic Load Balancer
* Auto Scaling
* MySQL RDs
* SNS for alerts
