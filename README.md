# mongodb
MongoDB cluster creation and deployment
---------------------------------------------------------
---------------------------------------------------------
TASK1: Create vpc and 3 subnets and attach the subnets to the vpc.

  1. Login to aws console , create keypair with the name - Mango.db
  2. create vpc with parameter-values
      => IPv4 CIDR block - 10.0.0.0/16
      => VPC name - vpc-123456789
      => Public subnet's IPv4 CIDR - 10.0.0.0/24, , 10.0.32.0/19
      => Availability Zone - us-east-1a
      => Subnet name - subnet-123
      => Public subnet's IPv4 CIDR - 10.0.64.0/19
      => Availability Zone - us-east-1b
      => Subnet name - subnet-456
      => Public subnet's IPv4 CIDR - 10.0.64.0/19
      => Availability Zone - us-east-1c
      => Subnet name- subnet-789

  3. On AWS console create Subnets with name tag subnet-123, subnet-456, subnet-789 and attach those subnet to vpc-123456789

  4. Create a folder in s3 bucket.

        S3 folder structure - demomongodb/template

  5. Create the stack for deploying mongodb cluster on the AWS using cloud formation, save it in s3 bucket.

        S3 bucket url - https://s3.amazonaws.com/demomongodb/template/template5

        Description-
        The template deploys 3 Centos mongodb instances with (ami-02e98f78) on the vpc-123456789 (with subnets subnet-123,
        subnet-456, subnet-789).
        Each of the instances is attached to 1TB EBS.

   6. Mongodb cluster deployment steps

      => Select cloudformation on aws console.
      => select create stack
      => choose a template (specify an amazon s3 template url)
          https://s3.amazonaws.com/demomongodb/template/template5
      => navigate through select (vpc-123456789, subnet-123, subnet-456, subnet- 789, 1000GB EBS, [3 Centos7-(ami-02e98f78),
      m4.large mongoDB instances]) and create the stack.

    7. On AWS console select route 53 create "DNS name = test.com" and attach it to vpc-123456789.

TASK 2: Create a Docker container with MongoDB version 3.4 and exposing the standard port. Logs should be written in a mounted volume.

   Run the Commands
   cd <<Path To my Dockerfile>>
   docker build -t myname/mongodb .
   docker run -d -p 27017:27107 -v ~/log/mongodb/:/var/log/mongodb/ myname/mongodb

   mongodb logs are avaiable at ~/log/mongodb/

TASK 3: Create github repository and push the files.

url : https://github.com/nethark1/mongodb
username - nethark1
password - nethraRK$25


Files pushed onto git

  1.Cloudformation template file "template5".

  2.keypair "mangodb.pem"

  3.Dockerfile to build MongoDB container images "Dockerfile.dms".
