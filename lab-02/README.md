# S3 Mini Lab Projects

## Goal
The goal of this project is to familiatize participants with Amazon S3(Simple Storage Servoice) concepts, create and manage S3 buckets, upload objects, enable versioning, set persmissions for public access and implements lifecycle policies

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

### Upload an object into this bucket
We will create a sample text file to contain "Welcome to uploading file to bucket" and upload to the bucket
- click the Upload button a page will appear, add the file and click on upload
  ![lab02pics4](images/lab02pics4.png)
  ![lab02pics5](images/lab02pics5.png)
- The screenshot below shows the file was uploaded successfully
   ![lab02pics6](images/lab02pics6.png)

## Step 2
### Enabling versioning
By default the bucket versioning is disabled
![lab02pics7](images/lab02pics7.png)
- To enable versioning, click on the edit button, select enable option and save changes
 ![lab02pics8](images/lab02pics8.png)
- Now we modify the content of the file and upload it again. A new version is show below by enabling show versions
  ![lab02pics9](images/lab02pics9.png)
  ![lab02pics10](images/lab02pics10.png)
  
## Step 3
### Content view and permissions setting
In the permissions tab of the bucket, you would observe that block all public access is enabled

![lab02pics11](images/lab02pics11.png)
- Click on Edit button and uncheck the "Block all public access" option, Save changes and confirm
  
- ![lab02pics12](images/lab02pics12.png)

This action we took ensure that file be accessible online. The next action involves creating bucket policy to specify action the public would have/perform on the file. 
- Click on the Edit button and click on policy generator
- Select the "Type of Policy" as "S3 Bucket Policy"
- Set the "Effect" to "Allow", specify the "Principal" as "*", which means all users.
- Choose the action "Get object" and "Get object version"
- In the field of Amazon Resource Name (ARN), type the ARN of your bucket and add by "/*" after the ARN. e.g arn:aws:s3:::first-s3-bucket-024/*
- Click on "Add statement" then click on generate policy
  
![lab02pics14](images/lab02pics14.png)
- Copy the policy, navigate to the bucket policy tab and paste
  
![lab02pics14](images/lab02pics14.png)
- Click on save changes
- We can view the different version of the file
  
Old version
![lab02pics15](https://github.com/user-attachments/assets/e97525a4-fb2f-457d-8b87-60c7668d5ee6)
![image](https://github.com/user-attachments/assets/c6e5f503-4052-4038-97a1-db3b3c8c3f3e)

New version
![lab02pics16](https://github.com/user-attachments/assets/e2187760-5fb3-4cde-b2d6-a20380de4cfb)
![image](https://github.com/user-attachments/assets/6ea98c90-e02e-40bf-bbbe-3b2e5ac670b6)


