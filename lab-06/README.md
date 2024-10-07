# AWS RDS Mini project

## Goal

To have understanding of AWS RDS and how to setup and manage databases and perform task like provisioning, backups, and scaling. Also users will learn about essential database security measures and user access control to protect sensitive information. Also will be look into troubleshooting techniques and performance optimization strategies, utilizing tools like Amazon CloudWatch to monitor database health.


**Login to AWS Console**
- Login to AWS console, navigate to the search bar input RDS and select
- On the left sidebar select Databases and click on Create database
- Select Standard create as database creation method
- For the Engine select MySQL option
- For the Engine Version, select the latest version
- Select the free tier templates
- Provide the DB instance name and select the master username for the database
- For the credential management select Self managed
- Enter the master password, and ensure its kept in safe place for access usage
- Choose DB instance class as db.t3.micro
- Leave the other configuration setting. Next select the VPC created earlier
- Select Public access as Yes
- For VPC security group select Choose existing
**Note**: Ensure that the security group attached to the database allows inbound traffic on port 3306. You can set up inbound rule for MySQL/Aurora on port 3306 if it is not currently configured
- Select any Availability Zones and click on Create database
- 
The database is created successfully

- Proceed by selecting the database you created
- On the Connectivity & security tab, select the Endpoint and document it alongside the username and password created earlier for the database.
- Connect to your EC2 instance using SSH to login and execute the necessary commands for setting up MySQL

- To download the RPM, use wget t download the package
```
sudo wget https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm

```
To install the RPM after downloading
```
sudo yum localinstall mysql57-community-release-el7-11.noarch.rpm
```
To import the GPG (GNU Privacy Guard) key for MySQL packages for verifying the integrity and authenticity of the packages
```
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
```

Now we can install the MySQL server with

```
sudo yum install mysql-community-server
```

Start the MySQL service and enable it to start on boot
```
systemctl start mysqld.service
systemctl enable mysqld.service
systemctl status mysqld.service
```

Now, connecting your RDS to ec2 instance,

```
mysql -h [Endpoint] -P [Port] -u [Username] -p[Password]
mysql-h my-rds-database.nomolos006yfd.ap-southeast-1.rds.amazonaws.com -P 3306 -u admin -pgatogrowfast-database
```
Note: Ensure there are no spaces between "-p" and your password. For example, if your password is "gatogrofast-database," it should be written as "-pgatogrowfast-database".

To view all databases, run:
SHOW DATABASES;
To use the database you have created, execute:
USE mysql;
To show tables inside the database,
SHOW TABLES;





