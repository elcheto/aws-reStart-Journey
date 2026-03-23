### Objectives
In this lab, I will:

- Create a new log file for process listings
- Use the top command
- Establish a repetitive task that runs your previous auditing commands once a day


### TASK 1: SSH Connection Guide (macOS & Linux)
Note: These steps are for Mac and Linux only. Windows users should skip to the next section.

1. Download Credentials: * Click the Details drop-down above and select Show.

Click Download PEM to save labsuser.pem.

Copy the PublicIP address, then close the panel (X).

2. Prepare the Key: * Open your terminal and navigate to your download folder:
bash cd ~/Downloads 

Restrict file permissions (required for SSH):

chmod 400 labsuser.pem

3. Connect via SSH:

Run the following command, replacing <public-ip> with the address you copied:

ssh -i labsuser.pem ec2-user@<public-ip>
Type yes when prompted. No password is required.

<img width="500" height="658" alt="Screenshot 2026-03-23 at 13 37 45" src="https://github.com/user-attachments/assets/7842f0ef-5c86-4471-bfc8-adc103d522ed" />


### Task 2: Exercise - Create List of Processes
In this exercise, I create a log file from the ps command. This log file should be added to the SharedFolders section:

Create a log file named processes.csv from ps -aux and omit any processes that contain root user or contain "["or"]" in the COMMAND section.

To validate that you are in the /home/ec2-user/companyA folder, enter pwd and press Enter. 

If you are not in this folder, enter cd companyA and press Enter.

View all processes running on the machine and filter out the word root by typing sudo ps -aux | grep -v root | sudo tee SharedFolders/processes.csv and pressing ENTER.

Validate your work by typing cat SharedFolders/processes.csv and pressing ENTER.

<img width="500" height="200" alt="Screenshot 2026-03-23 at 13 48 16" src="https://github.com/user-attachments/assets/01d25656-9c84-4bce-bde7-e1ce6807adcc" />

### Task 3: Exercise - List the processes using the top command
In this exercise, I will use the top command:

Run the top command to display processes and threads that are active in the system.
Observe the outputs of the top command.
In the main terminal run the command top and press ENTER:

top
The top command is used to display the system performance and lists the processes and threads active in the system. The output of the top command should look similar to the picture below:

<img width="400" height="400" alt="Screenshot 2026-03-23 at 13 50 57" src="https://github.com/user-attachments/assets/eb27932c-ff2f-4f91-92ed-bad2e9426049" />

To quit top, hit q and press ENTER.

I can also run top with the following options to find the usage and version information:

top -hv

### Task 4: Exercise - Create a Cron Job

In this exercise, I will create a cron job that will create an audit file with ##### to cover all csv files:

Cron is a command that runs a task on a regular basis at a specified time. This command maintains the list of tasks to run in a crontab file, which you create in this task. You create a job that creates the audit file with ##### in order to cover all .csv files. When you enter the crontab -e command, you are taken to an editor where you then enter a list of steps of what the cron daemon will run. The crontab file includes six fields: minutes, hour, day of month (DOM), month (MON), day of Week (DOW), and command (CMD). These fields can also be denoted with asterisks. Once this command runs, you can verify your work.

To validate that you are in the /home/ec2-user/companyA folder, enter pwd and press Enter.

To create a cron job that creates the audit file with ##### to cover all .csv files, enter sudo crontab -e and press Enter to enter the default text editor.

Press i to enter insert mode, and press Enter.

For the first line, enter SHELL=/bin/bash and press the Space bar.

For the second line, enter PATH=/usr/bin:/bin:/usr/local/bin and press Enter.

For the third line, enter MAILTO=root and press Enter.

For the last line, enter 0 * * * * ls -la $(find .) | sed -e 's/..csv/#####.csv/g' > /home/ec2-user/companyA/SharedFolders/filteredAudit.csv

My terminal:


To save and close the file, press ESC. Then enter :wq and press Enter.
To validate your work, enter sudo crontab -l and press Enter. Inspect the crontab file to ensure that it matches the text exactly, as the following output shows:

<img width="500" height="500" alt="Screenshot 2026-03-23 at 13 59 54" src="https://github.com/user-attachments/assets/63a49a8f-00f4-44d7-abbb-53dd33f1085f" />



