### Objectives
In this lab, I will:

- Create a new log file for process listings
- Use the top command
- Establish a repetitive task that runs your previous auditing commands once a day


### TASK 1: SSH Connection Guide (macOS & Linux)
Note: These steps are for Mac and Linux only. Windows users should skip to the next section.

# 1. Download Credentials: * Click the Details drop-down above and select Show.

Click Download PEM to save labsuser.pem.

Copy the PublicIP address, then close the panel (X).

# 2.Prepare the Key: * Open your terminal and navigate to your download folder:
bash cd ~/Downloads 

Restrict file permissions (required for SSH):

Bash
chmod 400 labsuser.pem
# 3.Connect via SSH:

Run the following command, replacing <public-ip> with the address you copied:

Bash
ssh -i labsuser.pem ec2-user@<public-ip>
Type yes when prompted. No password is required.

### Task 2: Exercise - Create List of Processes
In this exercise, I create a log file from the ps command. This log file should be added to the SharedFolders section:

Create a log file named processes.csv from ps -aux and omit any processes that contain root user or contain "["or"]" in the COMMAND section.

To validate that you are in the /home/ec2-user/companyA folder, enter pwd and press Enter. 

If you are not in this folder, enter cd companyA and press Enter.

View all processes running on the machine and filter out the word root by typing sudo ps -aux | grep -v root | sudo tee SharedFolders/processes.csv and pressing ENTER.

Validate your work by typing cat SharedFolders/processes.csv and pressing ENTER.

 
