In this lab expercise  I learnt the cloud connectivity and Linux command-line efficiency. It focused on two primary skill sets: establishing a secure remote connection to a cloud environment and performing core data manipulation tasks using standard Unix utilities.

AWS Linux Fundamentals Lab
This lab provides a hands-on introduction to connecting to an Amazon Linux EC2 instance and performing essential text-processing tasks via the command line.

🚀 Getting Started
# 1. Access the AWS Console
Start Lab: Click Start Lab and wait for the status to show Ready.

Open Console: Click the AWS button to open the management console in a new browser tab.

Setup: Arrange your browser tabs side-by-side to view instructions and the console simultaneously.

Note: Access is restricted to specific services required for this lab.

# 2. Connect via SSH (macOS/Linux)
Select Details > Show and download the labsuser.pem file.

Note the PublicIP address provided in the credentials window.

Open your Terminal and navigate to your downloads folder:

Bash
cd ~/Downloads
Update file permissions and connect (replace <public-ip> with your actual IP):

Bash
chmod 400 labsuser.pem
ssh -i labsuser.pem ec2-user@<public-ip>
Type yes when prompted to authorize the connection.

💻 Lab Tasks

## Task 1: The tee Command
Use tee to write output to both the screen and a file simultaneously.

Bash
hostname | tee file1.txt
ls  # Confirm file1.txt was created
## Task 2: Pipes and Sorting
Create a dataset and practice reordering and filtering information.

Create File: Run cat > test.csv, paste the content below, and press CTRL+D.

Plaintext
Factory, 1, Paris
Store, 2, Dubai
Factory, 3, Brasilia
Store, 4, Algiers
Factory, 5, Tokyo
Sort: sort test.csv

Filter: grep Paris test.csv

## Task 3: The cut Command
Extract specific columns from a delimited file.

Create File: Run cat > cities.csv, paste "City, State" entries (e.g., Dallas, Texas), and press CTRL+D.

Extract City: Use the comma as a delimiter to extract the first field:

Bash
cut -d ',' -f 1 cities.csv
Task 4: Stream Editing with sed
Use sed to perform search-and-replace operations within your files.

Bash
# Replaces the first comma with a period in both files
sed 's/,/./' cities.csv
sed 's/,/./' test.csv
