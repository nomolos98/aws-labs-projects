# VPC Mini Lab Projects

## Goal
The goal of this project is to have the understanding of Virtual Private Cloud(VPC), create and configure VPC, subnet, internet gateway, NAT gateway and VPC peering. Enable internet connectivity securely within a VPC, Implement outbound internet access through the NAT gateway, and establish direct communication between VPCs using VPC peering.

## Step 1
### Login to AWS Console
Goto [AWS Console](https://console.aws.amazon.com/) and login with your credentials. Navigate to the search bar on the AWS console and search and select S3. Another page will appear, locate and click "Create bucket" button

![lab02pics2](images/lab02pics2.png)

### Create the bucket
The create bucket page will appear, provide a unique name for the bucket. Ensure the following
- ACLs Disabled is selected
- Block public access option is enabled
- Bucket versioning disabled
- click on create bucket, and bucket will be created successfully with no object inside it

![lab02pics3](images/lab02pics3.png)

