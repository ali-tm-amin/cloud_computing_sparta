## S3 and AWS CLI
* Simple Storage Service
* shh into machine using AWS key
* if you couldn't, go to security tab and select security group add port 22, as a new inbound rule

*run these comands*
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

![](/images/Autoscaling_LoadBalancing.png)



