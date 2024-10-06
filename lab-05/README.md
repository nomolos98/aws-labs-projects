# Working with Amazon EC2  Application Load Balancer(ALB) and Auto Scaling Groups

## Goal
To have understanding concepts of ALB and Auto scaling Grpups and gain practical knowledge in setting up ALB to evenly distribute incoming traffic accross multiple servers
and configure Auto scaling groups to automatically adjust the no of instances based on demand ensuring application availability

## Step 1
### Login to AWS Console
- Goto [AWS Console](https://console.aws.amazon.com/) and login with your credentials. Navigate to the search bar on the AWS console and search and select EC2.
- Create and EC2 instance and launch using SSH

## Step 2: Create Load Balancer and Target group
We will be seting up target groups for different target instance to show how load balancer connect them all.

**Creating Load balancer**
- On the EC2 page scroll to Load Balancers on the left sidebar and click on Create load balancer
- On the Application Load Balancer option section click Create button

Provide details for ALB
- Provide name for the load balancer
- Select Internet-facing as the scheme
- Select IPv4 as the IP address type
- Select the VPC created earlier in our VPC mini lab
- Select the Availability Zone and choose the public subnet created earlier

**NB**: The subnet is not considered public subnet until we associate the route table which we gave path for the internet gateway.

- For the Listerner HTTP:80 select the target group we created earlier
- Now that we are done click Create load balance

Using Command prompt you can test network connectivity by pinging the public IP adderess of the instances

- From Load balancer page, copy the DNS of the load balancer and paste in new tab of browser.
- Confirm and observe if the load balancer is evenly distributing workload across all 3 instances

Creating Auto scalling group
