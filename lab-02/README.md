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
- 


![lab-001-scrn-02](images/lab-001-scrn-02.png)

Select *Amazon Linux 2 AMI*. An AMI is a template that contains the software configuration (operating system, application server, and applications) required to launch your instance. In this first lab, we will stick to the x86 architecture.

![lab-001-scrn-03](images/lab-001-scrn-03.png)


