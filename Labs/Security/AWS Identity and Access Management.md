AWS Identify and Access Management
------
**Objectives**
After completing this lab, Ive learnt to:
-	Create and apply an IAM password policy
-	Explore pre-created IAM users and user groups
-	Inspect IAM policies as applied to the pre-created user groups
-	Add users to user groups with specific capabilities active
-	Locate and use the IAM sign-in URL
-	Experiment with the effects of policies on service access

-----
IAM can be used for the following:
-	_Manage IAM users and their access:_ You can create users and assign them individual security credentials (access keys, passwords, and multi-factor authentication devices). You can manage permissions to control which operations a user can perform.
-	_Manage IAM roles and their permissions:_ An IAM role is similar to a user in that a role is an AWS identity with permission policies that determine what the identity can and cannot do in Amazon Web Services (AWS). However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.
-	_Manage federated users and their permissions:_ You can activate identity federation to allow existing users in your enterprise to access the AWS Management Console, to call AWS application programming interfaces (APIs), and to access resources without the need to create an IAM user for each identity.
----- 
_**Task 1: Creating an account password policy**_

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/6cbac8a9-f870-43c5-be58-38a5f42f5abb" />

&nbsp;

 On the dashboard under _account settings_, I clicked “edit”
<img width="940" height="306" alt="image" src="https://github.com/user-attachments/assets/c80a71b8-9d2e-4638-ac5d-02671167a70f" />

&nbsp;

My new password policies:
<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/04ea116d-46fd-4437-94f4-f6d542005751" />

&nbsp;

<img width="940" height="330" alt="image" src="https://github.com/user-attachments/assets/2dba5bea-2514-47bb-bf23-e464594b1f87" />

-----
_**Task 2: Explore users and user groups**_

Available users:
<img width="940" height="260" alt="image" src="https://github.com/user-attachments/assets/1ce90a5e-0ea4-4cf1-b7bf-d57c4631bcb0" />

&nbsp;

Available user groups:
<img width="900" height="200" alt="image" src="https://github.com/user-attachments/assets/a9425f6f-1767-46b1-8628-82e5233a027d" />

------
A **policy** defines what actions are allowed or denied for specific AWS resources. This policy grants permission to list and describe information about Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudWatch, and Amazon EC2 Auto Scaling. This ability to view resources but not modify them is ideal for assigning to a support role.
The following is the basic structure of the statements in an IAM policy:
- **Effect** indicates whether to **Allow** or **Deny** the permissions.
- **Action**specifies the API calls that can be made against an AWS service (for example, cloudwatch:ListMetrics).
- **Resource** defines the scope of entities covered by the policy rule (for example, a specific Amazon Simple Storage Service [Amazon S3] bucket, EC2 instance, or  which means any resource).
- 
**NOT SHOWN

-----
_**Task 3: Add users to user groups**_

_Add user-1 to the ec2 admin_
<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/1a3887f6-b4e2-4340-8284-2045d47383ae" />

&nbsp;
In the Users tab, you see that user-1 has been added to the group.
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/20841af6-6ca7-46f6-b6bc-b0fc3b8f8b8e" />

&nbsp;
_User 2 added to  ec2 support_
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/36ab0e6f-62a0-4951-a0f3-36b0c022fbd0" />

_User 3 added to s3 support_
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/7ac139ab-079e-499f-941a-d9094d609b1c" />

------
_**Task 4: Sign in and test user permissions**_

On the dashboard a link is provided. I copied the link and opened a new incognito tab to test the user permissions
<img width="494" height="400" alt="image" src="https://github.com/user-attachments/assets/abb135ff-9b13-4d6b-809c-bfe8a5c19b9c" />

------
**User 1**

User 1 is not able to see S3 buckets as they have not been added to the group.
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/ec9d64af-8378-4e82-b4dd-96f5e2bb9cc0" />

&nbsp;

----
**User 2**

<img width="470" height="400" alt="image" src="https://github.com/user-attachments/assets/4710b95d-3cea-499d-9200-0df7609bdd30" />

&nbsp;

User 2 is able to see an EC2 instance because they have read-only permissions. However, aren’t able to make any changes to Amazon EC2 resources.
<img width="900" height="239" alt="image" src="https://github.com/user-attachments/assets/44b959b8-06bc-4993-a25d-6b5a95b88f15" />


User 2 is not able to stop the instance as the only have read permissions.
<img width="900" height="290" alt="image" src="https://github.com/user-attachments/assets/fa94508f-9b54-4d5a-aa34-b313a1db3e67" />


User 2 doesn’t have access to list and view s3 buckets
<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/fbdf0b2d-54d3-4d64-a305-8fac5ca27798" />

---
User 1 was able to stop the EC2 instance as they have the permission to do so
<img width="940" height="200" alt="image" src="https://github.com/user-attachments/assets/9552065e-8ab7-4e9d-a4d6-365c714527c1" />

-------
I have successfully:
-	Created and applied an IAM password policy
-	Explored pre-created IAM users and user groups
-	Inspected IAM policies as applied to the pre-created user groups
-	Added users to user groups with specific capabilities active-
-	Located and used the IAM sign-in URL
-	Experimented with the effects of policies on service access
 



