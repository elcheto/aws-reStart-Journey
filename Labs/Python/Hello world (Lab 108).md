## Creating a "Hello, World" Program

Overview: Welcome to Intro to Programming! You’ll be using Python for these labs. Today, you’re going to write and run your very first program.
Estimated Time: 45 minutes

### 1. Launch the AWS Cloud9 IDE
Click Start Lab at the top of these instructions. Wait for the status to say Ready, then close the panel.

Click AWS to open the Management Console (be sure to allow pop-ups).

Go to Services > Cloud9, find the reStart-python-cloud9 card, and click Open IDE.

Note: If prompted, select Discard for setting changes and No for third-party content.

### 2. Set Up Your Python File
Go to File > New From Template > Python File.

Clear the file: Delete any sample code currently in the template.

Go to File > Save As..., name it hello-world.py, and save it in the /home/ec2-user/environment directory.

### 3. Check Your Environment
Click the + icon in the IDE and select New Terminal.

Type pwd to confirm you are in the correct directory.

Check your Python versions by entering:

python --version

python3 --version

Note: We will be using Python 3.6.x for this course.

### 4. Write & Run "Hello, World"
In your hello-world.py file, type the following:

Python
print("Hello, World")
Go to File > Save.

Click the Run (Play) button at the top of the window.

Look at the bottom pane to confirm it printed: Hello, World

Great job! I’ve officially written your first Python program.
