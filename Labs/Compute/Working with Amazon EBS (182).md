Working with Amazon EBS
# Lab overview
Amazon Elastic Block Store (Amazon EBS) is a scalable, high-performance block-storage service that is designed for Amazon Elastic Compute Cloud (Amazon EC2). In this lab, you learn how to create an EBS volume and perform operations on it, such as attaching it to an instance, creating a file system, and taking a snapshot backup.

 <img width="500" height="297" alt="Screenshot 2026-03-23 at 14 37 48" src="https://github.com/user-attachments/assets/8b0bc6aa-278e-4dce-8ff1-3c6ed593b3f9" />


Schematic diagram showing an EC2 instance with an attached EBS volume and a snapshot created from the EBS volume 

 

# Objectives
By the end of this lab, I will be able to do the following:

- Create an EBS volume.

- Attach and mount an EBS volume to an EC2 instance.

- Create a snapshot of an EBS volume.

- Create an EBS volume from a snapshot.

## Accessing the AWS Management Console
At the top of these instructions, choose  Start Lab to launch your lab. 

Tip: If you need more time to complete the lab, choose  Start Lab again to restart the timer for the environment.

The status of the lab resources is be displayed on the upper-left corner:

AWS  indicates that AWS lab resources are currently being created.

AWS  indicates that AWS lab resources are ready.

Wait for the lab to be ready before proceeding.

At the top of these instructions, choose AWS  to open the AWS Management Console on a new browser tab. The system automatically signs you in.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 14 45 42" src="https://github.com/user-attachments/assets/be22584e-296f-4f33-af78-33b41079001b" />


### Task 1: Creating a new EBS volume
In this task, I created and attached an EBS volume to a new EC2 instance.

1. On the AWS Management Console, in the Search bar, enter and choose EC2 to open the EC2 Management Console.
2. In the left navigation pane, choose Instances.
An EC2 instance named Lab has already been launched for your lab.
3. Note the Availability Zone for the Lab instance. It looks similar to the following: us-west-2a
4. In the left navigation pane, for Elastic Block Store, choose Volumes.
You see an existing (8 GiB) volume that the EC2 instance is using.
5. Choose Create volume, and configure the following options:
Volume type: Choose General Purpose SSD (gp2).
Size (GiB): Enter 1. 
Availability Zone: Choose the same Availability Zone as your EC2 instance (which is us-west-2a in this case).
6. In the Tags -optional section, choose Add tag, and configure the following options:
Key: Enter Name.
Value: Enter My Volume.
7. Choose Create volume. 
A new volume appears with the status of Creating in the Volume state column. This status soon changes to Available. You might need to choose Refresh  to see your new volume.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 14 48 42" src="https://github.com/user-attachments/assets/a668a15e-efa2-46d0-8bf1-a4aae5b9569c" />


<img width="500" height="300" alt="Screenshot 2026-03-23 at 14 48 52" src="https://github.com/user-attachments/assets/69404eda-7e8a-4cc4-845c-9b50de7a3868" />
