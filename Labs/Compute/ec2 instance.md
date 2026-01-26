This lab provided me with a basic overview of launching, resizing, managing, and monitoring an Amazon EC2 instance.

**Amazon Elastic Compute Cloud (Amazon EC2)** is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.
Amazon EC2's simple web service interface allows you to obtain and configure capacity with minimal friction. It provides complete control of your computing resources and lets you run on Amazon's proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

---
In the lab I will demonstrate:
-	Launching a web server with termination protection enabled
- Monitoring the EC2 instance
-	Modify the security group that the web server is using to allow HTTP access
-	Resize the Amazon EC2 instance to scale
- Test termination protection
-	Terminate the EC2 instance
 ----
1. Firstly, I navigate to the AWS management console, in the left pane I clicked on instances. I will create my instance with the name Web Server.
 <img width="800" height="240" alt="Screenshot 2026-01-26 200439" src="https://github.com/user-attachments/assets/b586a438-ee48-4f45-bd9d-e9158cdc5fbc" />
 
My instance type is t3. micro. For now, I will proceed without a key pair.

<img width="800" height="240" alt="Screenshot 2026-01-26 200805" src="https://github.com/user-attachments/assets/25ddf506-5c6b-4ccd-819a-466483aec37f" />

---
**2. Configuring the Network Settings**

<img width="600" height="400" alt="Screenshot 2026-01-26 201011" src="https://github.com/user-attachments/assets/3f8935fd-9b9e-43fe-82e6-9c066b451384" />

Still in the *Network settings* pane, I’ve configured the Security Group as follows:
- *Security group name – required*: Web Server security group
-	*Description*: Security group for my web server
  
A security group acts as a virtual firewall that controls the traffic for one or more instances. When launching an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances. You can modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group.

---
**3. Configuring Advanced Details**

- Expand the *Advanced details* pane.
- Select the dropdown for *Termination protection*, then choose *Enable*.
<img width="799" height="200" alt="Screenshot 2026-01-26 201456" src="https://github.com/user-attachments/assets/c3d3965a-7e9c-4b85-9ceb-c7fddf3575ef" />

When launching an instance in Amazon EC2, you have the option of passing user data to the instance. These commands can be used to perform common automated configuration tasks and even run scripts after the instance starts.

- I copied the following commands and paste them into the User data text box.
<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/56b6e826-12bb-400c-8938-9d7e83649d1d" />

The script does the following:
-	Install an Apache web server (httpd)
-	Configure the web server to automatically start on boot
-	Activate the Web server
-	Create a simple web page

After completing the above steps, I clicked *launch instance*  in the right pane, and the following confirmation message appears:
<img width="940" height="140" alt="image" src="https://github.com/user-attachments/assets/4f8bd5fc-2325-4ab2-83ef-23ce6286052a" />

Below is my insance running with all checks passed:
<img width="800" height="120" alt="image" src="https://github.com/user-attachments/assets/47ac6102-60ea-4f91-a093-2d1a954b8748" />

---
**4. Monitoring the Instance**

Monitoring is an important part of maintaining the reliability, availability, and performance of my Amazon Elastic Compute Cloud (Amazon EC2) instances and AWS solution.
With instance status monitoring, you can quickly determine whether Amazon EC2 has detected any problems that might prevent your instances from running applications. Amazon EC2 performs automated checks on every running EC2 instance to find hardware and software issues.
-	Notice that all 3 checks have been passed.
To monitor, I clicked the Actions tab, selected Monitor and troubleshoot, then clicked ”Get instance Screenshot”. 
<img width="800" height="300" alt="image" src="https://github.com/user-attachments/assets/a0595659-a55d-4ed8-b3a9-4232da7c9b33" />

The results:

<img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/313d9abf-a995-4700-97e5-e4bd486b7a4b" />

This confirms that my instance has been created with no underlying issues and is running.

---
**5. Updating My Security Group and Access the Web Server**

- Copy the Public IPv4 address of the instance to your clipboard. Open a new tab in the web browser, paste the IP address you’ve copied, then press Enter.

- I can’t access my web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests. This is a demonstration of using a security group as a firewall to restrict the network traffic that is allowed in and out of an instance.
<img width="640" height="300" alt="image" src="https://github.com/user-attachments/assets/53c440e9-35d9-4e57-ac73-0d43db70dfdc" />

To correct this, I will now update the security group to permit web traffic on port 80.
In the left pane,  I navigated to Network and Security, then clicked security groups.

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/658334fb-4479-440b-80cc-13c5fec9623f" />

-	Select the Inbound rules tab.
The security group currently has no rules.
<img width="550" height="200" alt="image" src="https://github.com/user-attachments/assets/5aaa49e4-1ae0-4c81-a1ba-11e05fc6a23c" />

-Select *Edit inbound rules* then select *Add rule* and configure the rule with the following settings:
-	Type: HTTP
-	Source: Anywhere-IPv4
-	Select Save rules
<img width="800" height="200" alt="image" src="https://github.com/user-attachments/assets/e179b6db-1832-4f33-85d5-3e9da5d09a0d" />


Return to the web server tab that you previously opened and refresh the page.
I now see the message *Hello From Your Web Server!*
<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/17aab390-0fba-4b38-822f-205283d195be" />

---
**6.Resize Your Instance: Instance Type and EBS Volume**

As your needs change, you might find that your instance is over-utilized (too small) or under-utilized (too large). If so, you can change the instance type. 

**Stop Your Instance**

Before resizing an instance, you must stop it.
When you stop an instance, it is shut down. There is no charge for a stopped EC2 instance, but the storage charge for attached Amazon EBS volumes remains.
<img width="700" height="180" alt="image" src="https://github.com/user-attachments/assets/81c48879-0ddb-4a60-ba60-97936f1d1ada" />

I selected *stop instance* and the following text box appeared: 
<img width="800" height="320" alt="image" src="https://github.com/user-attachments/assets/58b45448-5a3b-44f6-83c3-d60a4ec275bf" />

I Clicked stop. my instance will perform a normal shutdown and then will stop running.
 - Wait for the Instance State to display stopped.
<img width="800" height="300" alt="image" src="https://github.com/user-attachments/assets/a502ceb7-c068-423a-82a9-49af3445fb1d" />

---
**7. Changing The Instance Type to t3.small**
-	In the *Actions*  menu, select *Instance Settings Change Instance Type*, then configure, and select the new instance type.
-	Choose *Change instance type*
When the instance is started again it will be a t3.small, which has twice as much memory as a t3.micro instance.
 <img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/cdb9ba6f-417a-48ed-bf0b-4911816c6aa3" />

 The instance type has been changed:
 
<img width="600" height="100" alt="image" src="https://github.com/user-attachments/assets/045ebcef-9b51-4720-a238-9531cfcda79f" />

---
**8. Resizing the EBS Volume**
-	In the left navigation menu, I clicked *Volumes* located under *Elastic Block Store.*
-	Then I selected the volume by checking the box, and navigate to the *Actions*  menu, select *Modify Volume*.
The disk volume currently has a size of 8 GiB. I  will now increase the size of this disk to size 10.
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/e1d784c9-63fb-4d62-882b-cfc5f3cea335" />

 **Stop The Instance**
 
Before you can resize an instance, it must be stopped.
When I stopped an instance, it is shut down. There is no charge for a stopped EC2 instance, but the storage charge for attached Amazon EBS volumes remains.
-	On the *EC2 Management Console*, in the left navigation pane, select Instances.
-	*Web Server* should already be selected.
-	Select* Instance state > Stop instance.*
My instance will perform a normal shutdown and then will stop running.
-	Wait for the *Instance State* to display stopped
	
**Changing the Instance Type**
 	
-	In the Actions  menu, select *Instance Settings Change Instance Type*, then configure:
-	*Instance Type:* t3.small
-	Choose Change instance type
When the instance is started again it will be a t3.small, which has twice as much memory as a t3.micro instance.
-	*Start the Resized Instance*

--- 
**9. Test Termination Protection**

The instance can be deleted when you no longer need it. This is referred to as **terminating**. You cannot connect to or restart an instance after it has been terminated.
In this section, I will use termination protection.
-	In left navigation pane, select Instances.
-	Select the Web Server instance by checking the box and navigate to the top and select Instance state  menu, select *Terminate (delete) instance*.
Note: There is a message that says: On an EBS-backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated. Storage on any local drives will be lost. It asks if I am sure that i want to terminate the instance. I selected the Terminate button.

Note:  The instance did not terminate and a red error message pops up at the top that says: Failed to terminate an instance: The instance may not be terminated. This is because it has termination protection enabled.
<img width="800" height="300" alt="image" src="https://github.com/user-attachments/assets/c644ce28-b80c-4ed7-ac61-ab9801b4c312" />

-	In the *Actions*  menu, select *Instance settings Change termination protection*.
-	Uncheck *Enable* followed by *Save*

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/86ac8b81-65ee-41b3-a67b-dd2115d69146" />

The instance can now be terminated.
-	In the Actions  menu, select Instance State Terminate instance.
-	Select Terminate
  
My instance has successfully tested termination protection and has been terminated.





