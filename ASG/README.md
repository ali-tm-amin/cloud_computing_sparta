# Auto Scaling Group ASG
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
## Autoscaling and Load Balancing instructions:
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
* 1- On the Choose launch template or configuration page, for Auto Scaling group name, enter my-first-asg
* 2. Choose Next.
The Choose instance launch options page appears, giving you options for launching On-Demand and Spot Instances (if you chose a launch template) and allowing you to choose the VPC network settings you want the Auto Scaling group to use.
* 3. In the Network section, keep VPC set to the default VPC for your chosen AWS Region, or select your own VPC. The default VPC is automatically configured to provide internet connectivity to your instance. This VPC includes a public subnet in each Availability Zone in the Region.
* 4. For Availability Zones and subnets, choose a subnet from each Availability Zone that you want to include. Use subnets in multiple Availability Zones for high availability.

  * 5. [Launch template only] In the Instance type requirements section, use the default setting (do not override the launch template) to simplify this step. For this tutorial, you will launch only one On-Demand Instance using the instance type specified in your launch template.

* 6. Keep the rest of the defaults for this tutorial and choose Skip to review.
* 7. On the Review page, review the information for the group, and then choose Create Auto Scaling group.
https://docs.aws.amazon.com/autoscaling/ec2/userguide/GettingStartedTutorial.html#gs-create-lt

## S3 and AWS CLI
* Simple Storage Service
* shh into machine using AWS key
* if you couldn't, go in security tab and select security group Ads port 22, new inbound rule
* `sudo apt-get update -y`
* `sudo apt-get upgrade -y`
* `sudo apt update -y`
* `sudo apt upgrade -y`
* install pip `sudo apt install python3-pip`
* check if you have `python3 --version` installed
* Install awscli `sudo apt install awscli`
* `python3 -m pip install awscli`
* `aws configure` will prompt AWS Access key ID, add it then ask for more credential info 
* to see the list of s3 content `aws s3 ls`
* Create a bucket make it mb `aws s3 mb s3://eng99-ali`
* check if your bucket exists `aws s3 ls`
* add a file to s3 buket you just created `aws s3 cp README.md s3://eng99-ali`
* delete the file `rm -rf README.md`
* copy file to local machine `aws s3 cp s3://<path_to_file>`
* to remove the s3 bucket run `aws s3 rb s3://eng99-ali --force`
## Using python Boto3
* `import boto3`
* s3_client =boto3.client('s3)
* Create a bucket `location = {'LocationConstraint': 'eu-west-1'} s3_client.create_bucket(Bucket="eng99-ali",CreateBucketConfiguration=location)`
* Upload a file `import os object_name = os.path.basename(file_name) s3_client.upload_file(file_name, bucket, object_name)`
* Retrieve content/file from S3 using python-boto3:

* Delete content using python-boto3: `s3 = boto3.resource('s3') s3.Object('your-bucket', 'your-key').delete()` 
* Download a file `s3.download_file('BUCKET_NAME', 'OBJECT_NAME', 'FILE_NAME')`
* Delete a bucket `s3.delete_object(<bucket_name>, <file_pathon_bucket>)`
 https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.Python.03.html
Using credential for EC2 instance metadata https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-credentials.html

< img scr="image/Autoscaling_LoadBalancing.png" width="80" >




