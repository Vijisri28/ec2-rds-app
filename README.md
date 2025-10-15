# ec2-rds-app
Connect an Amazon RDS database with a web app on EC2

📘 Project Title

Building and Connecting an Amazon RDS Database with an EC2 Web Application

🎯 Objective

Deploy a web application on Amazon EC2.

Connect the application to a cloud-based MySQL database on Amazon RDS.

Ensure high availability using multi-AZ deployment.

Demonstrate full CRUD (Create, Read, Update, Delete) operations.

🧰 Tools & AWS Services Used

Amazon EC2 – Web application hosting

Amazon RDS (MySQL) – Cloud database service

Amazon VPC – Network isolation

Subnets & DB Subnet Groups – Multi-AZ deployment

Security Groups – Control access

IAM – Permissions and roles

⚙️ Step-by-Step Tasks (Text + Screenshots)

1. VPC and Security Groups

Created a VPC named Lab VPC with public and private subnets.
<img width="1086" height="198" alt="VPC" src="https://github.com/user-attachments/assets/82bbb20a-c44a-4c38-a036-e23b7aeb85d6" />

Configured Security Groups:

WebServer SG: HTTP (80), SSH (22)
<img width="1108" height="316" alt="DB SecurityGroup" src="https://github.com/user-attachments/assets/1df184a7-727f-46fd-bfb9-45997b001ce6" />

DB SG: MySQL (3306) access from WebServer

2. DB Subnet Group

Created a DB Subnet Group for RDS with two private subnets from different AZs:

10.0.1.0/24 (Private Subnet 1)

10.0.3.0/24 (Private Subnet 2)

<img width="1067" height="266" alt="DB SubnetGroup" src="https://github.com/user-attachments/assets/7fb84b63-6034-49c1-bb54-df1b7aa48746" />

3. Create Amazon RDS Database

Engine: MySQL (latest)

DB Identifier: lab-db

Master Username: main | Password: lab-password

Instance Class: db.t3.medium

Storage: General Purpose SSD

Connected to Lab VPC & DB Security Group
<img width="1052" height="192" alt="Database" src="https://github.com/user-attachments/assets/45bd3f14-9827-46b0-867c-e936efe98674" />


4. Interact with Database via Web Application

Copied RDS Endpoint from RDS console.

Opened EC2-hosted web application using Public IP.
<img width="1173" height="469" alt="Interact with database via web application" src="https://github.com/user-attachments/assets/2a7e4c40-8aaf-4051-b87c-2500ab5b4a76" />

Entered database details: Endpoint, DB Name, Username, Password.

Clicked Submit → Successfully connected.

Tested CRUD operations: Add/Edit/Delete Contacts.
<img width="1144" height="409" alt="connect to RDS MYSQL database" src="https://github.com/user-attachments/assets/78ce69ad-ca79-4edf-bec2-a4c68250567c" />

5. Results

Web app successfully connected to RDS MySQL database.

All CRUD operations worked correctly.
<img width="1139" height="357" alt="Result" src="https://github.com/user-attachments/assets/d35221e1-74a1-4f0c-a2d0-1285ed74d3a1" />


Data automatically replicated to standby in another AZ for high availability.
