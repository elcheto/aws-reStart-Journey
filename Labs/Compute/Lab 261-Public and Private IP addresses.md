### Lab: Public vs. Private IP Addresses
Objectives
Investigate the customer scenario and identify networking issues.

Analyze the functional differences between public and private IP addresses.

Resolve the connectivity issue and provide best-practice recommendations.

Scenario
Customer: Jess, Cloud Admin (Fortune 500)
Issue: Two EC2 instances (A and B) are in the same VPC/Subnet. Instance B connects to the internet; Instance A does not.
Question: Can I use a public IP range (e.g., 12.0.0.0/16) for my new VPC?

##  Task 1: Investigate the Environment
Open AWS Console: Click Start Lab, wait for the status to reach "Ready," then click AWS.

Navigate to EC2: Search for EC2 in the top search bar.

Check Instances: Go to Instances in the left sidebar.

Compare Networking:

Select Instance A → Networking tab. Record the Public and Private IPv4.

Select Instance B → Networking tab. Record the Public and Private IPv4.


<img width="500" height="300" alt="3" src="https://github.com/user-attachments/assets/ccdc1a37-21fb-4f22-bbd8-a80456d9f569" />

<img width="500" height="300" alt="4" src="https://github.com/user-attachments/assets/720ea8a9-f869-4a2e-a816-81a593ecafb8" />


## Task 2: Connect via SSH (macOS)
Download Key: Select Details > Show above these instructions. Click Download PEM and save labsuser.pem.

Set Permissions: Open your Terminal and run:

Bash
cd ~/Downloads
chmod 400 labsuser.pem
Test Connections: Try to connect to both instances using their IP addresses:

Bash
ssh -i labsuser.pem ec2-user@<IP-ADDRESS>
Results & Findings
Why did Instance A fail? It only has a Private IP. Private IPs are not routable over the internet. To access it via SSH from your Mac, the instance must have a Public IP.

Public CIDR for VPCs: Using a public range like 12.0.0.0/16 for an internal VPC is not recommended. It can cause IP address conflicts with actual websites on the internet, making them unreachable from within your network. Always use RFC 1918 private ranges (e.g., 10.0.0.0/8, 172.16.0.0/12, or 192.168.0.0/16).

<img width="573" height="451" alt="Screenshot 2026-04-07 at 21 57 56" src="https://github.com/user-attachments/assets/0da864ad-5d48-44d0-8b90-25dcaaff1b4d" />


## Task 3: Summary for Customer
The Fix: Assign a Public IP to Instance A or use a NAT Gateway/Bastion Host.

The Advice: Do not use the 12.0.0.0/16 range for the VPC. Stick to private address space to avoid routing conflicts.

<img width="500" height="300" alt="1" src="https://github.com/user-attachments/assets/230cc768-216c-445e-8274-44108ded2750" />

<img width="500" height="300" alt="2" src="https://github.com/user-attachments/assets/efc5c28a-0041-4cad-a925-da4613502dc0" />

