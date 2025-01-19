# AWS IAM Access Management
Hello, In this project you are going to create users, groups, and add permission policies in AWS Identity and Access Management (IAM) as per the requirements and ensure principle of least privilege.
## Learning Objectives
1. Understanding AWS IAM Basics
2. User Management
3. Group Management
4. Policy Management
5. Applying Access Controls
6. Custom Policy Development
7. Verifying IAM Configurations
8. Enhancing Security Awareness
## Prerequisites
1. Basic understanding of AWS services and the IAM console.
2. An active AWS account with administrative access.
3. Familiarity with JSON for writing custom policies.
4. Knowledge of access control concepts (e.g., users, groups, policies).
# Step 1:- Logging in to the Amazon Web Services Console.
Login to your AWS account using your AWS credentials
# Step 2:- Create IAM Users
1. Go to AWS managed console search bar and search - IAM

![IAM](https://github.com/avinash-jagtap/IAM-Access-Management.git)

2. CLick on - IAM
3. Click on - Users
4. Click on - Create user
    * Enter User name - AdminUser1
    #### Next
    * Tick Checkbox - Provide user access to the AWS Management Console.
    * Console password - Custom password 
    * Enter Password - Admin@004

        _Password Policy- 1. at least 8 characters long and 2. Include 3 char(A-Z with lower & Upper), at least 1 number(0-9), symbols ! @ # $ % ^ & * ( ) _ + -, (hyphen) = [ ] { } |_
    #### Next
5. Click on - create user

![AdminUser1](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/AdminUser1.png)

##### AdminUser1 user successfully created.
## Follow same steps and create reamining 3 users.
    - AdminUser2
    - DevUser1
    - DevUser2

![Users](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/Users.png)

##### All 4 users Successfully created. 
# Step 3:- Create IAM user groups.
### Admins
1. Click on user groups
2. Click on - create group 
3. Enter Group name - Admins
4. Add users - AdminUser1 & AdminUser2 
5. Attach permissions policies - AdministratorAccess

![Admins](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/Admin%20Group%20Creation.png)

    _Now your Admins have full access_
6. Click on - create User group
##### Admin user Group created Succefully.
### Developers 
1. Click on user groups
2. Click on - create group 
3. Enter Group name - Developers
4. Add users - DevUser1 & DevUser2 
5. Attach permissions policies - IAMReadOnlyAccess

![Developers](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/Dev%20Group%20creation.png)

    _Now your Developers have IAMread only access._
6. Click on - create User group
##### Admin user Group created Succefully.
# Step 4:- Access Management
_Now your users and user groups are created now you can manage access create and attach inline policies to specific user or group._
#### Inline Policy for DevUser1
1. Go to users
2. Select - DevUser1
3. click on - Add permissions
4. Click on - create inline policy 
    * Select Service - S3 
    * Select action - Allow
    * Select - All write actions
    * Resource - All
    * Enter policy name - S3-Write-access
    * Click on - Create policy 
5. Go to DevUser1 and verify in - Permissions policies

![DevUser1-inline](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/DevUser1%20InlinePolicy%20-%20S3.png)

_Note:- The inline policy named S3-Write-access grants the DevUser1 user write access to all S3 resources._
#### Inline Policy for DevUser2
1. Go to users
2. Select - DevUser2
3. click on - Add permissions
4. Click on - create inline policy 
    * Select Service - EBS 
    * Select action - Allow
    * Select - All write actions
    * Resource - All
    * Enter policy name - EBS-Write-access
    * Click on - Create policy 
5. Go to DevUser2 and verify in - Permissions policies

![DevUser2-inline](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/DevUser2%20Inlinepolicy%20-%20EBS.png)

_Note:- The inline policy named EBS-Write-access grants the DevUser2 user write access to all EBS resources._
##### Both developers, DevUser1 and DevUser2, can perform read operations on IAM service however, DevUser1 has write permissions only for S3, and DevUser2 has write permissions only for EBS.
#### Inline Policy for Developers groups
1. Go to user groups
2. Select - Developers
3. click on - Add permissions
4. Click on - create inline policy 
    * Select Service - Lambda
    * Select action - Allow
    * Select - All write actions
    * Resource - All
    * Enter policy name - Lambda-Write-access
    * Click on - Create policy 
5. Go to Developers and verify in - Permissions policies 

![Developers-inline](https://github.com/avinash-jagtap/IAM-Access-Management/blob/master/Images/Lambda%20Inline%20Policy.png)

##### The Lambda-Write-access inline policy grants DevUser1 and DevUser2 unrestricted write access to all Lambda functions, allowing creation, modification, and deletion. To enhance security, restrict resources or actions based on specific needs.
# Summary
This project implements AWS IAM role-based access control by creating four users (AdminUser1, AdminUser2, DevUser1, DevUser2) and two groups (Admins and Developers). Admins have unrestricted access to all services using the AdministratorAccess policy, while Developers have read-only access to IAM service with additional specific write permissions: DevUser1 can write to S3, and DevUser2 can write to EBS. Custom inline policies, such as S3-Write-access, EBS-Write-access and Lambda-Write-access, are applied to manage permissions precisely. The configuration demonstrates best practices by adhering to the principle of least privilege and ensuring that users only have the permissions required for their roles.