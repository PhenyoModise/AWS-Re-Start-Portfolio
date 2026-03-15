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

In this task, I need to log into an existing EC2 instance.

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/1e06bea2-04c8-4ac8-823c-6a4a3b10b589" />

After inserting the needed information for the connection, I clicked open and entered my username.

<img width="400" height="500" alt="Image" src="https://github.com/user-attachments/assets/a3d86788-bde2-44c1-92ca-91e2c738672e" />

-------
_**Task 2: Install the AWS CLI on a Red Hat Linux instance**_

To write the downloaded file to the current directory, I ran the following curl command with the -o option:

**Curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"**

<img width="600" height="500" alt="Image" src="https://github.com/user-attachments/assets/d2c957d5-a9b5-4eb4-9836-0acabd71072a" />

&nbsp;

To unzip the installer, I ran the unzip command with the **-u option**. In this command, the unzip command prompts you to overwrite any existing files. To skip these prompts, the command includes the -u option.

**unzip -u awscliv2.zip**

The result:

<img width="600" height="556" alt="Image" src="https://github.com/user-attachments/assets/36803d79-5e4a-4e58-a113-0192a92e66b8" />

&nbsp;

I ran the below command to install the program. This sudo command grants write permissions to the directory. The installation command in the code snippet uses a file named install in the unzipped aws directory to install the AWS CLI. 

**sudo ./aws/install.**
