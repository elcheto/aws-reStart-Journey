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

### Task 2: Attaching the volume to an EC2 instance
I can now attach my new volume to an EC2 instance.

1. Select My Volume.
2. From the Actions menu, choose Attach volume.
3. From the Instance dropdown list, choose the Lab instance.
For the Device name field select /dev/sdb. Commands that you run later in this lab include this device identifier. 
4. Choose Attach volume.
The Volume state of your new volume is now In-use.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 14 57 49" src="https://github.com/user-attachments/assets/6dd5c001-fd94-44c7-918f-1a761245d0af" />
<img width="500" height="300" alt="Screenshot 2026-03-23 at 14 58 00" src="https://github.com/user-attachments/assets/c7be5b02-da79-4a11-aeb1-00a01f763db4" />

### Task 3: Connecting to the Lab EC2 instance
In this task, I use EC2 Instance Connect to connect to the Lab EC2 instance. 

1. On the AWS Management Console, in the Search bar, enter and choose EC2 to open the EC2 Management Console.
2. In the navigation pane, choose Instances.
3. From the list of instances, select the Lab instance.
4. Choose Connect.
5. On the EC2 Instance Connect tab, choose Connect.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 01 20" src="https://github.com/user-attachments/assets/500f1397-c26b-485d-bbae-c848617cd92a" />

This option opens a new browser tab with the EC2 Instance Connect terminal window.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 01 39" src="https://github.com/user-attachments/assets/ae410ddb-2348-44ac-8b0d-97fa392c74aa" />

### Task 4: Creating and configuring the file system
1. In this task, I add the new volume to a Linux instance as an ext3 file system under the /mnt/data-store mount point.

To view the storage that is available on your instance, in the EC2 Instance Connect terminal, run the following command:

df -h

<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 03 46" src="https://github.com/user-attachments/assets/313f2125-c4ab-45c5-bdbf-422c5a833aa8" />

These results show the original 8 GB disk volume. My new volume is not yet shown.

2. To create an ext3 file system on the new volume, run the following command:

sudo mkfs -t ext3 /dev/sdb

<img width="500" height="250" alt="Screenshot 2026-03-23 at 15 07 08" src="https://github.com/user-attachments/assets/d5b1c8b7-006a-4720-b0de-44914f5e12cc" />


3. To create a directory to mount the new storage volume, run the following command:

sudo mkdir /mnt/data-store

4. To mount the new volume, run the following command:

sudo mount /dev/sdb /mnt/data-store
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
The last line in this command ensures that the volume is mounted even after the instance is restarted.

5.To view the configuration file to see the setting on the last line, run the following command:

cat /etc/fstab

6. To view the available storage again, run the following command:

df -h
The output now contains an additional line similar to the following: /dev/nvme1n1

<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 08 59" src="https://github.com/user-attachments/assets/5195f52f-940d-4466-abcc-d2532625eceb" />


7. To create a file and add some text on the mounted volume, run the following command:

sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"

8. To verify that the text has been written to your volume, run the following command:

cat /mnt/data-store/file.txt
   <img width="500" height="160" alt="Screenshot 2026-03-23 at 15 11 03" src="https://github.com/user-attachments/assets/ad8c4c63-972d-46e4-87c1-28683c655c50" />

   The output displays the text that this command copies to the file. 
   
### Task 5: Creating an Amazon EBS snapshot
In this task, I created a snapshot of your EBS volume.

Amazon EBS snapshots are stored in Amazon Simple Storage Service (Amazon S3) for durability. New EBS volumes can be created out of snapshots for cloning or restoring backups. Amazon EBS snapshots can also be shared among Amazon Web Services (AWS) accounts or copied over AWS Regions.

1. On the EC2 Management Console, choose Volumes, and select My Volume.
2. From the Actions menu, choose Create snapshot.
3. In the Tags section, choose Add tag, and then configure the following options:
Key: Enter Name.
Value: Enter My Snapshot.
<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 14 37" src="https://github.com/user-attachments/assets/c874dcb2-928b-4ceb-aab3-af97c54a0fa8" />

5. Choose Create snapshot.

 <img width="500" height="300" alt="Screenshot 2026-03-23 at 15 14 46" src="https://github.com/user-attachments/assets/f6bc9054-d4ea-476a-b9da-5177438eb0c2" />

7. In the left navigation pane, choose Snapshots.
The Snapshot status of your snapshot is Pending. After completion, the status changes to Completed. Only used storage blocks are copied to snapshots, so empty blocks do not use any snapshot storage space.
<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 15 46" src="https://github.com/user-attachments/assets/27873183-3f3f-4d3a-a0c2-05776857317a" />

9. In your EC2 Instance Connect terminal window, to delete the file that you created on your volume, run the following command:

sudo rm /mnt/data-store/file.txt
7. To verify that the file has been deleted, run the following command:
ls /mnt/data-store/file.txt

<img width="500" height="80" alt="Screenshot 2026-03-23 at 15 17 17" src="https://github.com/user-attachments/assets/df3b1ebe-50e7-44e1-9f62-9c356a43a0c4" />

### Task 6: Restoring the Amazon EBS snapshot
If you need to retrieve data stored in a snapshot, you can restore the snapshot to a new EBS volume.

## Task 6.1: Creating a volume by using the snapshot
1. On the EC2 Management Console, select My Snapshot.
2. From the Actions menu, choose Create volume from snapshot.
3. For Availability Zone, choose the same Availability Zone that you used earlier.
4. In the Tags - optional section, choose Add tag, and then configure the following options:
Key: Enter Name.
Value: Enter Restored Volume.
5. Choose Create volume.
6. To see your new volume, in the left navigation, choose Volumes.
<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 22 20" src="https://github.com/user-attachments/assets/27f22a59-d065-4b1a-a2cf-d06f4e6c53d0" />

The Volume status of your new volume is Available.

## Task 6.2: Attaching the restored volume to the EC2 instance
Select Restored Volume.

1. From the Actions menu, choose Attach volume.
2. From the Instance dropdown list, choose the Lab instance.
3. For the Device name field, choose /dev/sdc. You use this device identifier in a later task.
4. Choose Attach volume.
The Volume status of your volume is now In-use.

<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 24 26" src="https://github.com/user-attachments/assets/df7d565b-372a-4521-bff4-4c64beb043c7" />


## Task 6.3: Mounting the restored volume
1. To create a directory for mounting the new storage volume, in the EC2 Instance Connect terminal, run the following command:

sudo mkdir /mnt/data-store2

2. To mount the new volume, run the following command:

sudo mount /dev/sdc /mnt/data-store2

3. To verify that the volume that you mounted has the file that you created earlier, run the following command:

ls /mnt/data-store2/file.txt

You should see the file.txt file.


<img width="500" height="300" alt="Screenshot 2026-03-23 at 15 25 45" src="https://github.com/user-attachments/assets/55a3fef4-3b7f-4897-8fc8-2cd11a28bb94" />
