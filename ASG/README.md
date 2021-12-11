# Auto Scaling Group ASG

![](/images/AWS_ASG_Diagram.jpeg)
## Monitoring & Alert Management
Automated Monitoring Tools:
* System status checks 
* Instance status checks
* Amazon CloudWatch alarms
* Amazon EventBridge
* Amazon CloudWatch Logs
* CloudWatch agent
* AWS Management Pack for Microsoft System Center Operations Manager
Manual Monitoring Tools:
* Amazon EC2 Dashboard shows:
  * Service Health and Scheduled Events by Region
  * Instance state
  * Status checks
  * Alarm status
  * Instance metric details (In the navigation pane choose Instances, select an instance, and choose the Monitoring tab)
  * Volume metric details (In the navigation pane choose Volumes, select a volume, and choose the Monitoring tab)
* Amazon CloudWatch Dashboard shows:
  * Current alarms and status
  * Graphs of alarms and resources
  * Service health status
* In addition, you can use CloudWatch to do the following:
  * Graph Amazon EC2 monitoring data to troubleshoot issues and discover trends
  * Search and browse all your AWS resource metrics
  * Create and edit alarms to be notified of problems
  * See at-a-glance overviews of your alarms and AWS resources
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_automated_manual.html
## Autoscaling and Load Balancing
*instructions:*
* Create Launch Template for auto scaling group(ASG)
* Create Auto load balancer
* ALB: Application Load Balancer
* Attach VPC with 3 subnet in 3 different AZs
* Configure SG for app
* All EC2 have Nginx installed on
* Regions eu-AZs

## Disaster Recovery Plan
* Hyprid cloud deployment- Fintech - banking
* Multi-Rigion deployment for large organisation
* Multi-cloud deployment, FCA; banks must have multi cloud deployments 

## Launch template
To create a launch template

* Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.

On the navigation pane, under INSTANCES, choose Launch Templates.

* Choose Create launch template. Enter a name and provide a description for the initial version of the launch template.

* Under Auto Scaling guidance, select the check box to have Amazon EC2 provide guidance to help create a template to use with Amazon EC2 Auto Scaling.
* Follow the link below for more instructions
* https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-launch-template.html

## Auto Scaling
To create an Auto Scaling group:
  - On the Choose launch template or configuration page, for Auto Scaling group name, enter my-first-asg
- Choose Next.
The Choose instance launch options page appears, giving you options for launching On-Demand and Spot Instances (if you chose a launch template) and allowing you to choose the VPC network settings you want the Auto Scaling group to use.
- In the Network section, keep VPC set to the default VPC for your chosen AWS Region, or select your own VPC. The default VPC is automatically configured to provide internet connectivity to your instance. This VPC includes a public subnet in each Availability Zone in the Region.

- For Availability Zones and subnets, choose a subnet from each Availability Zone that you want to include. Use subnets in multiple Availability Zones for high availability.

- [Launch template only] In the Instance type requirements section, use the default setting (do not override the launch template) to simplify this step. For this tutorial, you will launch only one On-Demand Instance using the instance type specified in your launch template.

- Keep the rest of the defaults for this tutorial and choose Skip to review.

- On the Review page, review the information for the group, and then choose Create Auto Scaling group.


### For ASG setup instructions follow the link:
https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg.html
https://docs.aws.amazon.com/autoscaling/ec2/userguide/GettingStartedTutorial.html#gs-create-lt
