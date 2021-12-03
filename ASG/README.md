## Monitoring & Alert Management
* https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_automated_manual.html
## Autoscaling and Load Balancing instructions:
* Create Launch Template for auto scaling group(ASG)
* Create Auto load balancer
* ALB: Application Load Balancer
* Attach VPC with 3 subnet in 3 different AZs
* configure SG for app
* All EC2 have Nginx installed on
* Regions eu-AZs

# Disaster Recovery Plan
* Hyprid cloud deployment- Fintech - banking
* Multi-Rigion deployment for large organisation
* Multi-cloud deployment, FCA; banks must have multi cloud deployments 

## Launch template
* https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchTemplates.html

## Auto Scaling
* https://aws.amazon.com/autoscaling/

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
