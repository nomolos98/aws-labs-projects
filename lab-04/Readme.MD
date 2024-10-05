# Security Groups and NACLs  Mini Lab Projects

## Goal
To have understanding fundamental components of AWS infrastructure, including how Secunty Groups control inbound and outbound traffic to EC2 instances, and now Network Access Control List(NACL) act as subnet-level firewalls, regulating traffic entering and exiting subriets. 

## Step 1
### Login to AWS Console
Goto [AWS Console](https://console.aws.amazon.com/) and login with your credentials. Navigate to the search bar on the AWS console and search and select EC2. 

![lab04pics1](images/lab04pics1.png)

## Step 2
### Create an EC2 Instance
You can go through our previous session on how to create an EC2 instances that would host our website.
![lab04pics2](images/lab04pics2.png)

For the security group configuration of this instance, the inbound rules only IPv4 SSH traffic on port 22 is permitted to access this instance. For outbound rule, all IPv4 traffic with any protocol on any port is allowed, meaning this instance has unrestricted access to anywhere on the internet.

![lab04pics3](images/lab04pics3.png)
![lab04pics4](images/lab04pics4.png)

Next, we test connectivity to the website using the public IP address assign to this instance. so enter the public IP to your browser, it will load with this site can't be reached.
The reason for this is because we haven't defined HTTP protocol for the security group to allow outside access into the instance
![lab04pics5](images/lab04pics5.png)

## Step 3
**To resolve this issue, so that data can be populated we create new security group**
- Create a new security group that allows traffic on HTTP port 80.
- Click the Security groups on the left sidebar, and click on create security group.
- Provide a name and description for the security group and select the VPC
- Click add rule
- Now select HTTP as the type, use 0.0.0.0/0 as the CIDR and click on create security group
- Next we attached the security group to our instance
- Goto the instance section on the left sidebar, click on Actions, select security and click Change security group
- Select the security group just created and click Add security group button
- The security groupis now added then click Save button
- Copy the public IP address and paste on the browser and you would be able to view data of your website

We can see how the rule allows the HTTP and SSH protocols to access the instance, and we are able to access the website


### Network Access Control List(NACL)

- On the search bar, search for VPC and click
- Goto Network ACLs on the left sidebar and click create network ACL
- Provide a name for the Network ACL
- Choose the VPC previously created, then click Create network ACL
- Select the network ACL just created and select the lnbound tab

**Note: By default the Inbound rules is denying all traffic from all ports. same goes for Outbound rules**

- For the Inbound tab, click on Edit inbound rules and click Add new rule
- Add the rule number, select the type, select source and specific if to Allow or Deny traffic
- Save the changes

**The NACL is currently not associated with any subnet, so let associate it**

- Select the NACL and click on Action and choose Edit subnet association
- Select your public subnet as the instance within the public subnet
- Save the changes

We can see the NACL is attachedd sussessfully to our public subnet and when we try to view the public IP on the browser, it display site can't be reached. 
Why is it not displaying even though we have permitted all traffic in the inbound rule of the NACL. The reason is that NACLs are stateless and they don't automatically allow return traffic. So the solution is to explicitly configure rules for both inbound and outbound traffic.





