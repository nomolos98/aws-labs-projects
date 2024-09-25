# VPC Mini Lab Projects

## Goal
The goal of this project is to have the understanding of Virtual Private Cloud(VPC), create and configure VPC, subnet, internet gateway, NAT gateway and VPC peering. Enable internet connectivity securely within a VPC, Implement outbound internet access through the NAT gateway, and establish direct communication between VPCs using VPC peering.

## Step 1
### Login to AWS Console
Goto [AWS Console](https://console.aws.amazon.com/) and login with your credentials. Navigate to the search bar on the AWS console and search and select VPC . 

![lab03pics1](images/lab03pics1.png)

### Create PVC
Another page will appear, click "Create VPC"
- Select VPC only option, specify CIDR block
- Click Create VPC button
  
![lab03pics2](images/lab03pics2.png)
The VPC created is as shown below
![lab03pics3](images/lab03pics3.png)

## Step 2
### Configuring subnet within the VPC
- Navigate to the Subnet link on the left sidebar and click
- The subnet page appears, click on create subnet
- 
![lab03pics4](images/lab03pics4.png)

- On the create subnet page (public subnet), select ID of the VPC we created earlier
- Enter the subnet name, choose available zone, and specify the IPv4 CIDR for the subnet
- Click Add new subnet button
  ![lab03pics5](images/lab03pics5.png)
  ![lab03pics6](images/lab03pics6.png)

We are creating a second subnet (private subnet), so repeat same steps and specify the following
- The subnet name, choose availability zone and provide IPv4 CIDR (e.g 10.0.7.0/24)
- Click create subnet button
  
  ![lab03pics7](images/lab03pics7.png)

We no whave the 2 completed subnets

![lab03pics8](images/lab03pics8.png)

## Step 3
### Creating Internet Gateways attached to VPC
- Navigate to Internet gateways on the left sidebar and click
- Next, click "Create Internet gateway" button
![lab03pics9](images/lab03pics9.png)

- Provide name for the internet gateway
- Click internet gateway button
![lab03pics10](images/lab03pics10.png)

- The internet gateway is successfully created, and it is currently detached(meaning not attached to a vpc and so there can't be any internet connectivity)
  ![lab03pics11](images/lab03pics11.png)

- Attach the internet gateway to the VPC
![lab03pics12](images/lab03pics12.png)
![lab03pics13](images/lab03pics13.png)

The internet gateway is now attached
![lab03pics15](images/lab03pics15.png)

Next we will be setting up Routing tables for internet coonectivity with the internet gateway.
![lab03pics14](images/lab03pics14.png)
-
## Step 4
### Creating Route table for connectivity
- Navigate to The Route table on the left sidebar and click
- Next, click "Create Route table" button
![lab03pics16](images/lab03pics16.png)
- Enter name of the route table and select the VPC
- Click on Create route table button
![lab03pics17](images/lab03pics17.png)

- Select Subnet association tab and click on Edit subnet associations
![lab03pics18](images/lab03pics18.png)
- Select the pulic subnet and click on save association
![lab03pics19](images/lab03pics19.png)


