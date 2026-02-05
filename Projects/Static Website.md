FreshlyGround Cafe ☕
-------

Description:
This project elaborates hosting a static website using AWS services.

Concepts Demonstrated:
- Static website hosting
- Cloud architecture basics
- Deployment principles

**Group Name: The Cloud Crew🎈**

----
**Problem Statement for FreshlyGround Cafe’s Cloud Migration**

FreshlyGround, a beloved local cafe, faces operational challenges due to outdated on-premises systems. The lack of a robust online presence hinders its ability to attract and retain customers in today’s digital landscape.

**Objective:**

To overcome these challenges, FreshlyGround aims to migrate its IT infrastructure to the cloud. The primary goals are to enhance operational efficiency, improve customer engagement, and provide a seamless experience for patrons.

**Proposed Solution:** 

1.	Cloud Infrastructure Migration: 
- FreshlyGround plans to migrate its IT systems to a reliable cloud service provider, specifically Amazon Web Services (AWS).
2.	Online Presence Enhancement:
  - The cafe will develop a cloud-hosted website to bolster its online presence. This website will allow customers to view the menu and prices conveniently.
----
**Key Services:** 🚀

_Amazon S3 (Simple Storage Service):_
- Benefits:
  
💠Highly Scalable: Amazon S3 can handle varying data volumes, from gigabytes to petabytes, without compromising performance.

💠Reliable: Designed for 99.999999999% durability and 99.99% availability, ensuring data safety and accessibility.

💠Secure: Robust security features, including encryption at rest and in transit, access control policies, and integration with AWS Identity and Access Management (IAM).

 - Features:

💠Easy Integration: Seamlessly integrates with other AWS services.

💠Cost-Effective: Provides cost savings compared to traditional hosting.

💠Custom Domain Support: Allows custom domain names for branding.

_Static Website Hosting:_

Freshly Ground can directly host static websites from an S3 bucket. This cost-effective approach serves static content (HTML, CSS, JavaScript, and images) without requiring a separate web server.
I have designed AWS architecture for Freshly Ground Cafe’s cloud migration. This is a high-level architecture that incorporates the specified service:

<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/be938d00-83c8-4de3-b5e2-b52e76bace10" />

-------
_1. Compute Services_
Amazon EC2 (Elastic Compute Cloud)

- Host Freshly Ground’s applications, web servers, and databases and provide scalable compute capacity.
AWS Lambda
- Execute serverless functions in response to events (e.g., new orders, website visits).
  
_2. Storage Services_

Amazon S3 (Simple Storage Service)
- Store static content (HTML, CSS, images) for the cafe’s website and host the website directly from S3 buckets.
Amazon EBS (Elastic Block Store)
-	Provide block-level storage volumes for EC2 instances and store data persistently.

  
_3. Migration Services_

AWS Database Migration Service (DMS)
- Replicate data from on-premises databases to RDS or DynamoDB.
- Perform schema conversion if needed.
  
AWS Server Migration Service (SMS)
- Migrate VMs from on-premises to EC2 instances.

 --------
Hosting the website🎯
------
After we created the website, we then went on to host it onto Amazon S3.
-	Firstly launch the AWS consol, search ‘s3’ then click on 'create bucket'
  <img width="930" height="280" alt="image" src="https://github.com/user-attachments/assets/90cf4034-720b-479c-9d4f-cd0715b78d5f" />

  &nbsp;
- Under bucket name I wrote 'ourfreshlygroundcafe2026'
<img width="930" height="280" alt="image" src="https://github.com/user-attachments/assets/4f2701a6-0c5f-4c9d-8c7b-860e6754fb0f" />

  &nbsp;
-	As shown, public access was blocked so I had to enable public access, then click ‘Create bucket’
  <img width="930" height="280" alt="image" src="https://github.com/user-attachments/assets/39e6fe58-513e-4d87-b137-a1b0ede55ae7" />
 &nbsp;

 - The bucket has successfully been created.
<img width="930" height="270" alt="image" src="https://github.com/user-attachments/assets/4028ac10-25b6-4df3-ab46-0ad987782e2a" />

 &nbsp;
-	I clicked the bucket name, navigated to the permissions tab and saw that ‘Block all public access was blocked. I edited this and enabled ‘public access’
  <img width="930" height="280" alt="image" src="https://github.com/user-attachments/assets/d1cd5d8e-74d2-421b-be71-862c76d8585f" />
  <img width="930" height="280" alt="image" src="https://github.com/user-attachments/assets/eb0c7a47-aade-46ac-aa6b-54b340e60037" />
  
 &nbsp;
 - Thereafter, I scrolled down. Under bucket policy, clicked edit to add a policy.
-	Added a policy then saved the changes.
  <img width="905" height="280" alt="image" src="https://github.com/user-attachments/assets/36912bfa-dbd6-4295-a61d-71a02026433d" />
  
 &nbsp;
  - Under properties> static website hosting, I clicked 'edit'
    <img width="930" height="139" alt="image" src="https://github.com/user-attachments/assets/fcfc75f7-539e-4b28-b558-b87bbb5fc613" />
   &nbsp;

  - Enabled static website hosting, added an index document, followed by the other supporting files of the website then saved changes.
  <img width="860" height="280" alt="image" src="https://github.com/user-attachments/assets/b7ef05c8-7c1e-4182-9ad9-100763fe780b" />
  <img width="850" height="380" alt="image" src="https://github.com/user-attachments/assets/fbee7070-9319-4fcf-8cd1-353fc99dd312" />
  
&nbsp;
  - The website has successfully been hosting and is running on Amazon S3.

http://ourfreshlygroundcafe2026.s3-website.af-south-1.amazonaws.com 
<img width="930" height="196" alt="image" src="https://github.com/user-attachments/assets/305eca50-fadf-4dc1-b456-713b43a9e9da" />

------------


  &nbsp;
