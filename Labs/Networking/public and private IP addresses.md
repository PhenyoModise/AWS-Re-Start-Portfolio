Public and private IP addresses
-----

**Objectives:**

In this lab, i will:
- Summarize and investigate the customer scenario
- Analyze the difference between a private and public IP address
- Develop a solution to the customer's issue in this lab
- Summarize and describe my findings

-------
1. I have navigated to the Amazon EC2 dashboard. In the left navigation menu, I chose Instances. This option took me to my current EC2 instances.
   <img width="940" height="205" alt="image" src="https://github.com/user-attachments/assets/f18c4c77-9eef-46aa-8f88-391a7fa281ca" />

2.  Select the check box next to instance A. At the bottom of the page, choose the _Networking tab_, and note the Public and Private IPv4 addresses:
   
- Instance A has only the private IP address
  <img width="940" height="226" alt="image" src="https://github.com/user-attachments/assets/cb7e4b7a-9832-4e6a-b41b-aa1d9c2278e9" />


- Instance B has both the private and public IPv4 address
  
<img width="940" height="262" alt="image" src="https://github.com/user-attachments/assets/7c918229-d01e-4352-b1d0-14f0863fb397" />

----
**Using SSH to connect to an Amazon Linux EC2 instance**

1. I connected to a Amazon Linux EC2 instance using an SSH utility to perform all of these operations.
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/6520ad4f-4922-4509-9b32-04dbac8cb512" />

&nbsp;

After connecting to the Amazon Linux EC2 instance, I noticed that I was not able to connect to Instance A because it was assigned only a private IP address. Private IP addresses cannot be accessed from outside the VPC. Since I was attempting to connect from outside the VPC, the connection was not possible.
However, I was able to connect to Instance B because it had a public IP address assigned to it. The public IP allowed access from outside the VPC, which enabled me to successfully use the SSH utility to connect to the instance.

**Conclusion:**

In this lab, I investigated the customer’s environment and applied troubleshooting techniques that allowed me to resolve the customer’s issue. During the scenario, I discovered that the customer’s EC2 instance (Instance A) needed a public IP address in order to connect to the internet. I tested this by attempting to use an SSH utility to connect to the instance.
I found that private IP addresses are used only within the VPC and cannot establish a connection to the internet. Because Instance A only had a private IP address, it was not accessible externally. I also learned that using a public range of IP addresses for a VPC can cause complications, such as receiving replies from unrelated external resources, which can lead to networking conflicts and unexpected behaviour.






