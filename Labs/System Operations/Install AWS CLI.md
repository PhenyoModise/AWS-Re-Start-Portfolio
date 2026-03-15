Install and Configure the AWS CLI
-----

**Lab overview**

The AWS Command Line Interface (AWS CLI) is a command line tool that provides an interface for interacting with products and services from Amazon Web Services (AWS).

-------
**Objectives**
-	Install and configure the AWS CLI.
-	Connect the AWS CLI to an AWS account.
-	Access IAM by using the AWS CLI.

------
_**Task 1: Connect to the Red Hat EC2 instance by using SSH**_

1. In this task, I need to log into an existing EC2 instance.

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/1e06bea2-04c8-4ac8-823c-6a4a3b10b589" />

2. After inserting the needed information for the connection, I clicked open and entered my username.

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/a3d86788-bde2-44c1-92ca-91e2c738672e" />

-------
_**Task 2: Install the AWS CLI on a Red Hat Linux instance**_

1. To write the downloaded file to the current directory, I ran the following curl command with the -o option:

**Curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"**

<img width="600" height="500" alt="Image" src="https://github.com/user-attachments/assets/d2c957d5-a9b5-4eb4-9836-0acabd71072a" />

&nbsp;

2. To unzip the installer, I ran the unzip command with the **-u option**. In this command, the unzip command prompts you to overwrite any existing files. To skip these prompts, the command includes the -u option.

**unzip -u awscliv2.zip**

The result:

<img width="600" height="556" alt="Image" src="https://github.com/user-attachments/assets/36803d79-5e4a-4e58-a113-0192a92e66b8" />

&nbsp;

3. I ran the below command to install the program. This sudo command grants write permissions to the directory. The installation command in the code snippet uses a file named install in the unzipped aws directory to install the AWS CLI. 

**sudo ./aws/install.**

<img width="500" height="165" alt="Image" src="https://github.com/user-attachments/assets/1d003122-91a2-4f2a-811b-972b98a5bf0f" />

&nbsp;

4. My CLI is now working

<img width="500" height="539" alt="Image" src="https://github.com/user-attachments/assets/63655975-0360-49b5-9d6a-9255b990a04f" />

-----
_**Task 3: Observe IAM configuration details in the AWS Management Console**_

In this section, I observe the IAM configuration details for the EC2 instance in the AWS Management Console. 

1. In the AWS Management Console, I navigated to the IAM service.

<img width="500" height="353" alt="Image" src="https://github.com/user-attachments/assets/5bc02c0c-8efa-46b0-8e50-571fd0e520f9" />

&nbsp;

2. In the navigation pane, under **Users**, I chose **awsstudent**.
 
3. this lead me to the **Permissions** tab. 
<img width="500" height="400" alt="Image" src="https://github.com/user-attachments/assets/b6b5389d-46d2-43ef-97a3-178963619149" />

&nbsp;

4. This **lab_policy** document is formatted in JSON. The IAM policy grants the awsstudent user access to specific AWS services in this account.

<img width="500" height="370" alt="Image" src="https://github.com/user-attachments/assets/8ddc6a8a-dc4c-4c83-a8de-7ddc650f85e1" />

&nbsp;

5. In the **Security credentials** tab, I navigated to the **Access keys** section to  locate the awsstudent user's access key ID

<img width="500" height="378" alt="Image" src="https://github.com/user-attachments/assets/339d6e95-61a9-4357-bf29-8f1a52edf4be" />

------
_**Task 4: Configure the AWS CLI to connect to your AWS Account**_

1. In the SSH session terminal window, I ran the configure command for the AWS CLI:
**aws configure**

2. At the prompt, I configured the following:
- AWS Access Key ID: 
- AWS Secret Access Key:
- Default region name:  
- Default output format: 

(NOT SHOWN)

----
_**Task 5: Observe IAM configuration details by using the AWS CLI**_

In this section, I observe the IAM configuration details for the EC2 instance using the AWS CLI.
1. In the terminal window, test the IAM configuration by running the following command:

**aws iam list-users**

A successful test shows a JSON response that includes a list of IAM users in the account.

<img width="500" height="600" alt="Image" src="https://github.com/user-attachments/assets/23f257f2-5dbd-4185-9e80-e3a64efccfe6" />

&nbsp;

The following command lists IAM policies and filters customer managed policies:

<img width="506" height="443" alt="Image" src="https://github.com/user-attachments/assets/a8b3b518-f875-49de-90c6-92543ab7bee6" />

------
_**Conclusion**_

The following has been completed:
-	Installed and configured the AWS CLI
-	Connected the AWS CLI to an AWS account
-	Accessed IAM by using the AWS CLI
