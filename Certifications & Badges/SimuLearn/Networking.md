Network Architecture
---------
Objective: Architected a secure, multi-tier VPC for a simulated financial client using AWS SimuLearn.

--------
Key Implementations:
* VPC Segmentation: Configured public and private subnets with custom IPv4 routing.
* Secure Ingress/Egress: Deployed an Internet Gateway for web traffic and a NAT Gateway to allow private instances to update securely without internet exposure.
* Defense-in-Depth: Enforced strict traffic control using a combination of Security Groups (instance-level) and NACLs (subnet-level).


<img width="1000" height="770" alt="image" src="https://github.com/user-attachments/assets/c9fbb831-8965-40b9-98dc-74c4e1856841" />

<img width="1265" height="695" alt="Screenshot 2026-02-16 100343" src="https://github.com/user-attachments/assets/7815dbe6-9761-4d31-af1d-c0c4e802bc50" />
