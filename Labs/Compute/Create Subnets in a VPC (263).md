### Lab Overview: Designing and Deploying a Scalable AWS VPC
Purpose and Objective
The primary goal of this lab was to act as an AWS Cloud Support Engineer assisting a startup owner, Paulo, in building a secure and scalable networking foundation. The objective was to design a Virtual Private Cloud (VPC) that adheres to specific architectural requirements:

Utilizing the RFC 1918 private IP range (specifically the 192.x.x.x block).

Supporting a minimum of 15,000 private IP addresses for the headquarters' future growth.

Establishing a Public Subnet with a capacity for at least 50 usable IP addresses for operational tasks.

Through this process, I gained hands-on experience with the AWS Management Console, CIDR math, and the logical isolation of cloud resources.

## Steps Taken to Create the Infrastructure
# 1. Requirements Analysis & CIDR Calculation
To meet the customer's request for 15,000+ IPs using a 192.168.x.x range, I performed the following calculations:

VPC Sizing: A /16 provides 65,536 IPs, while a /18 provides 16,384 IPs. Since 16,384 is the smallest block that satisfies the 15,000-IP requirement, I selected 192.168.0.0/18 for the VPC CIDR.

Subnet Sizing: The customer required 50 IPs for the public subnet. A /26 prefix provides 64 addresses, which comfortably covers the requirement while accounting for the 5 IP addresses AWS reserves by default in every subnet.

# 2. Launching the VPC Wizard
I accessed the VPC Dashboard within the AWS Management Console and utilized the VPC Wizard to ensure all foundational components (like Route Tables and Internet Gateways) were created consistently.

<img width="700" height="350" alt="Screenshot 2026-04-08 at 13 43 24" src="https://github.com/user-attachments/assets/c3de6d1e-1d08-412f-9715-75fa589f1fbe" />


# 3. Configuring the Network Parameters
I manually configured the VPC settings to match the calculated requirements:

VPC Name: Named the resource First VPC for easy identification.

IPv4 CIDR Block: Assigned 192.168.0.0/18.

Public Subnet Configuration: * Named the subnet Public subnet.

Assigned the CIDR block 192.168.1.0/26.

Set the Availability Zone to "No Preference" to allow AWS to optimize placement.

<img width="700" height="350" alt="Screenshot 2026-04-08 at 13 46 49" src="https://github.com/user-attachments/assets/80e3b50d-3eb7-4d2d-b495-b9d8a66bf03c" />


# 4. Verification and Validation
After clicking Create VPC, I verified the setup by navigating to the "Your VPCs" section of the console. I confirmed that:

The VPC status was "Available."

The Internet Gateway was correctly attached, allowing the public subnet to reach the outside world.

The private IP schema remained within the boundaries of RFC 1918, ensuring internal security.

<img width="700" height="350" alt="Screenshot 2026-04-08 at 14 05 28" src="https://github.com/user-attachments/assets/70dbe9dc-5f45-4c14-973d-e3406b60bb8d" />


### Key Findings
This lab demonstrated that proper IP planning is critical before deployment. By choosing a /18 for the VPC and a /26 for the public subnet, I provided the customer with a solution that is both space-efficient and capable of supporting their specific headcount requirements without wasting an excessive amount of the private address space.

<img width="700" height="350" alt="Screenshot 2026-04-08 at 14 06 16" src="https://github.com/user-attachments/assets/1cafead5-c0f8-4f94-800c-06daaed18365" />

