# VPC Mini Lab Projects

## Goal
The goal of this project is to have the understanding of Virtual Private Cloud(VPC), create and configure VPC, subnet, internet gateway, NAT gateway and VPC peering. Enable internet connectivity securely within a VPC, Implement outbound internet access through the NAT gateway, and establish direct communication between VPCs using VPC peering.

## Step 1
### Login to AWS Console
Goto [AWS Console](https://console.aws.amazon.com/) and login with your credentials. Navigate to the search bar on the AWS console and search and select VPC . 

![lab03pics1](images/lab03pics1.png)

### Create VPC
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
- 
![lab03pics10](images/lab03pics10.png)

- The internet gateway is successfully created, and it is currently detached(meaning not attached to a vpc and so there can't be any internet connectivity)
- 
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

- Select the route table created, click the Routes tab and click edite routes
![lab03pics20](images/lab03pics20.png)
- Click the Add route, make the Destination as 0.0.0.0/0 (means every IPv4 address can access the subnet)
- On Target field select internet gateway and select the internet gateway we created earlier
- Saves changes

![lab03pics21](images/lab03pics21.png)

Now, the route table have been configured to route traffic to the internet gateway, allowing connectivity to the internet

![lab03pics22](images/lab03pics22.png)

## Step 5
### Creating NAT Gateway
We will enable Outbound Internet access through NAT Gateway, so we attach the NAT gateway to the subnet and route table
- Navigate to NAT gateways on the left sidebar and click 
- Next, click "Create NAT gateway" button and provide the following details

![lab03pics23](images/lab03pics23.png)

- Click on Create NAT gateway and is created successfully
  
![lab03pics24](images/lab03pics24.png)

- Select the NAT gateway and click on the subnet link or better still goto the subnet page and click on the Route table tab

![lab03pics25](images/lab03pics25.png)

- Click on the route table ID and select the route table 

![lab03pics26](images/lab03pics26.png)

- Move to Routes tab and click on Edit route

![lab03pics27](images/lab03pics27.png)

- Click on Add routes and make Destination as 0.0.0.0/0
- 
![lab03pics28](images/lab03pics28.png)

- For target field select NAT gateway and select the NAT gateway we created earlier
- Click on save

![lab03pics29](images/lab03pics29.png)

- On the Subnet association tab, click Edit subnet association

![lab03pics30](images/lab03pics30.png)

- Select private sunbet and clisk Save association
- 
![lab03pics31](images/lab03pics31.png)

The subnet have been successfully attached to the route table

![lab03pics32](images/lab03pics32.png) 


### Footer Note:

**Internet Gateway:** Think of it like a door to the internet for your subnet. When you attach an Internet Gateway to a subnet, it allows the resources in that subnet like EC2 instances) to reach out to the internet and also allows internet traffic to reach those resources. It's like having a door both to enter and exit the subnet

**NAT Gateway:** Imagine it as a one-way street sign for your subnet's traffic. When you attach a NAT Gateway to a subnet, it lets the resources in that subnet (like EC2 instances) access the internet, but it doesn't allow incoming traffic from the internet to reach those resources, it's like the resources can go out to the internet, but the internet traffic can't directly come in

![image](https://github.com/user-attachments/assets/31e835b4-3c61-4d01-838a-84d4b2cc5375)

## Step 6
### VPC Peering
VPC peeering establishes network connection between  VPCs, allowing EC2 instances in one VPC to communicate with EC2 instances in the other VPC.
- Create two VPCs(let use same region)
- Navigate to Peering connections option on the left sidebar and click 
- Next, click "Create Peering connection" button and provide details
- Provide name for the VPC peering connection
- Select the requeser VPC
- Ensure you select same region since VPCs were created in same region
- select the acceptor VPC
- Click on create peering connection button
- In the Peering connection page, select Actions option on the far right side and click Accept request
- Click the Accept request button when done
- Select the acceptor VPC option on route table
- Select the Route table and navigate to Route tab
- Click on Edit routes, and click the add route button
- Goto the VPC page and select the requester VPC
- In the Details tab, check the IPv4 CIDR address( in this case 192.168.0.0/16) and select it and paste in the Destination field when adding Routes
- In the Target choose VPC peering and then choose the peering you earlier created
- Click save changes

- Next, copy the IPv4 CIDR of the acceptor VPC address(in this case 172.16.0.0/16)
- Select Route table and select the requester VPC and choose the Route Tab
- Then click Edit route and add route. Paste the CIDR in the Destination field, in target choose VPC peering and select the peering connection created earlier

Connection is sucessfully established, and resources in both the acceptor VPC and requester VPC can connect

In summary for understanding what we just build. Think of a VPC endpoint like a dedicated, secure tunnel between your house (VPC) and a library (AWS service) so instead of going through the bustling streets (public internet), you have a direct pathway from your nome to the library. This pathway ensures that only you and authorized users can access the library's resources, like books or documents, without exposing them to outside risks. It's a private, efficient way to access what you need, keeping your data safe from prying eyes on the Internet. Now, when you're backing up data from an EC2 instance to an S3 bucket, it usually goes over the intemet, whether the instance is in a public or private subnet. But if the data is sensitive, that means it's risiky because hackers could try to get it while it's traveling over the internet, that is VPC endpoint solves, bu cretaing private connections between the VPC and S3 and data doesn't go through the internet
