Network Hardening
------

“The developers at AnyCompany are in the initial phases of building an application primarily using AWS Lambda. Throughout the development process, they need an automated security tool that not only scans for vulnerable software packages but also scans within the code itself. You decide to utilize Amazon Inspector to fill this need.”

Amazon Inspector meets the requirements of being able to scan AWS Lambda functions by quickly responding to new deployments. It also automatically scans additional resources such as EC2 instances, Amazon ECRs within AnyCompany’s AWS account.

------
**Objectives**

In this lab I’ve learnt to :
- Activate Amazon Inspector.
- Analyze and interpret vulnerability findings.
- Remediate the vulnerabilities found by Amazon Inspector.
-----

**_Task 1: Activate the Amazon Inspector_**

In this section, I will activate and run the Amazon inspector service to continuously scan the Lambda functions.

In the AWS Management Console, in the search bar at the top, type and choose Inspector.
<img width="900" height="370" alt="image" src="https://github.com/user-attachments/assets/cb620def-9b96-473f-a1c8-4236cbd8e0bb" />

&nbsp;
<img width="900" height="270" alt="image" src="https://github.com/user-attachments/assets/af479f36-c556-4ecc-ba67-7efa98d0fb27" />

&nbsp;

I clicked on “Activate this account” and waited for the dashboard to appear with:
Environment coverage > Lambda functions at 100%
<img width="900" height="370" alt="image" src="https://github.com/user-attachments/assets/4fadb2a2-196b-4307-aaab-0f1e43178376" />

------

**_Task 2: Reviewing the inspected resources_**

While I waited for the scan to finish, I reviewed the current lab environment (the EC2 instance and the Lambda functions) to understand what specific resources are being scanned by Amazon Inspector.

_Reviewing Lambda functions_
-	From the Findings on the left, choose All findings.
-	Three rows are displayed, one for each vulnerability within Lambda function. The following key details were displayed:

o	Severity:Medium

o	Impacted resource shows you the affected Lambda function.

o	Title shows the reason for the finding. 
<img width="900" height="270" alt="image" src="https://github.com/user-attachments/assets/e6870974-ada8-4d84-ae7e-a44ba3ea3280" />

&nbsp;
I clicked the finding **CVE-2023-32681 - requests.** This opens a pane containing the vulnerability information.
<img width="880" height="300" alt="image" src="https://github.com/user-attachments/assets/e8f9fbc6-ba92-4994-b754-b604d0368402" />

---
Within the information pane, under the **Vulnerability details** section I chose the external link next to the Vulnerability ID.
The link opens a new browser tab to the vulnerability detail webpage from the **National Vulnerability Database (NVD)**, which is a repository of standardized vulnerability management data maintained by the National Institute of Standards and Technology (NIST). This page offers more detailed information about the vulnerability.

<img width="527" height="500" alt="image" src="https://github.com/user-attachments/assets/512f9ad6-d094-4036-9724-e32573448ff4" />
<img width="940" height="424" alt="image" src="https://github.com/user-attachments/assets/e095e911-cbf2-48fd-bfb9-dcb839c4cebc" />

---
Within the information pane, in the Remediation section:
The issue is that the **requests** package is vulnerable and outdated, and the recommendation is to upgrade the package. 
<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/79279d57-c4f1-4da3-a92a-86c864df65e8" />

---
**_Task 3: Remediating the vulnerabilities findings_**

In this section, I analyzed the findings reported by Amazon Inspector and interpret the vulnerability details. Firstly, by updating the Lambda functions to remediate the vulnerabilities. After updating the functions, you review the Amazon Inspector findings to confirm the vulnerability has been fixed.

_Remediating the Lambda function’s Package Vulnerabilities_
-	On the AWS Management Console, in the search box, search for and choose Lambda
-	From the list of Lambda functions, I selected the **get-request **function.
<img width="740" height="300" alt="image" src="https://github.com/user-attachments/assets/9306d306-4ca4-43e1-9ccf-965b15940384" />

Within the Lambda function code editor’s file browser, I navigated to **requirements.txt.**  and did the following:

-	Remove the version number and equal signs from requests==2.20.0 so that the line becomes only requests.
<img width="740" height="300" alt="image" src="https://github.com/user-attachments/assets/e22208ff-17f7-4c4e-b303-fe0c37e6f123" />

&nbsp;

The **requirements.txt** file tells AWS Lambda which Python packages are required to run a function. When no version number is specified, the latest version of the package will be installed by default. This ensures that the Lambda funtion uses the latest version of the package.
-	Deploy button to deploy the function.
A banner is displayed with the message Successfully updated the function get-request.
This latest deployment of the Lambda function will trigger Amazon Inspector to initiate a new scan of the function.
-	On the AWS Management Console, in the search box, search for and choose Amazon Inspector.
-	In the navigation pane at the left of the page, under **Findings**, select **All findings**.
-	In the findings dashboard, under finding status, change the selection from **Active to Closed.**
<img width="940" height="350" alt="image" src="https://github.com/user-attachments/assets/ab84bef2-44d5-431f-8fe1-96cc9537eabd" />

&nbsp;

-	In the list of closed findings, you see **CVE-2023-32681 - request**s. This confirms the successful remediation of the vulnerability.
_Note: It takes a few minutes for the scan to initiate and finish. _
-	In the navigation pane at the left of the page, under **Resources coverage**, I chose **Lambda functions**.
<img width="940" height="300" alt="image" src="https://github.com/user-attachments/assets/06faadb8-23d3-4458-bc9d-8962015cabd2" />

You see that the most recently scanned Lambda function has an updated timestamp.

---------


