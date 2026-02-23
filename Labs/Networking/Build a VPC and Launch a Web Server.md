Build a VPC and Launch a Web Server
----

**Overview:**
-	Create a virtual private cloud (VPC)
-	Create subnets
-	Configure a security group
-	Launch an Amazon Elastic Compute Cloud (Amazon EC2) instance into a VPC
------

_Step 1: Create the VPC_

In this task, I use the VPC Wizard to create a VPC, an internet gateway, and two subnets in a single Availability Zone. An internet gateway is a VPC component that allows communication between instances in my VPC and the internet.

VPC settings:

<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/ee7fc7bd-5ed6-457e-8fbd-25bb8aac5223" />

&nbsp;

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/ac54f974-45ee-4273-bf2e-affd04695bdd" />

&nbsp;

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/63e4677c-6f6d-48ad-9b5a-7c8aaf6cf927" />

&nbsp;

I’ve configured the preferred settings, named my VPC ,route tables, and subnets accordingly below.
<img width="700" height="370" alt="image" src="https://github.com/user-attachments/assets/a5b3a2d6-46b3-4198-86b1-8b8be792dbf4" />

&nbsp;

Click create vpc and wait for the following the all be checked.

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/b0fdcb69-5e84-4c0b-9201-e906ba9b1a49" />

&nbsp;

My VPC is now available for use:
<img width="900" height="190" alt="image" src="https://github.com/user-attachments/assets/56f1fa91-1777-4b32-bd81-2270203f56f7" />

-----
_Step 2_

In this task, I create two additional subnets in a second Availability Zone. This option is useful for creating resources in multiple Availability Zones to provide high availability.
<img width="940" height="86" alt="image" src="https://github.com/user-attachments/assets/d73f7c45-f040-40e5-b92e-d5c3348fe9ec" />

&nbsp;

I've associated the new subnets with routes.
<img width="940" height="200" alt="image" src="https://github.com/user-attachments/assets/32a795b8-419f-40f5-92e0-f501d2e590ef" />

&nbsp;

<img width="940" height="200" alt="image" src="https://github.com/user-attachments/assets/82c83d04-2057-4dfc-80e7-d29016a83ece" />

&nbsp;

My VPC now has public and private subnets configured in two Availability Zones:
<img width="860" height="400" alt="image" src="https://github.com/user-attachments/assets/ca8d608c-3842-4e4a-b93d-856854dc730d" />

-----
_Step 3: Create a VPC security group_

In this task, I have created a VPC security group, which acts as a virtual firewall for my instance. When you launch the instance, you associate one or more security groups with the instance. You can add rules to each security group that allow traffic to or from its associated instances.
<img width="800" height="320" alt="image" src="https://github.com/user-attachments/assets/e6cba1aa-6851-489b-8277-423a12238975" />

------
_Step 4: Launch a web server instance_

In this task, I launch an EC2 instance into the new VPC. I configure the instance to act as a web server.
<img width="800" height="200" alt="image" src="https://github.com/user-attachments/assets/ecfe48f4-2c3c-465b-afa6-4c9334b16b69" />

&nbsp;

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/80ef64bc-e2aa-408d-9eb4-7a67b40fcd91" />

 &nbsp;

Select the instance type: t3.micro and the key pair:
<img width="940" height="420" alt="image" src="https://github.com/user-attachments/assets/72790696-e64b-4b7a-bf31-9bc79c515f78" />

 &nbsp;

 Selected the security group I've previously made and inserted the user data:
 <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/2bd16b26-eb4f-4425-aeed-d9518e43e84e" />

 <img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/483a8b7d-3746-4181-b490-e79d4020c336" />

  &nbsp;

  Clicked on **Create Instance** after confirming my settings, then clicked on instances to view my instance.
  <img width="940" height="157" alt="image" src="https://github.com/user-attachments/assets/df0807f6-4eee-4dc0-a68a-554456ef9bf4" />

------
_Step 5: Connect to the web server running on the EC2 instance._

-	Select the check box for the instance and choose the **Details tab.**
-	copy the **Public IPv4 DNS value.**
-	open a new web browser tab, paste the Public IPv4 DNS value, 

The web server application loaded successfully, confirming the instance and VPC configuration were working correctly.
