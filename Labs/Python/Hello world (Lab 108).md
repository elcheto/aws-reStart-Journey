## Creating a "Hello, World" Program

Overview: Welcome to Intro to Programming! I’ll be using Python for these labs. Today, I am going to write and run my very first program.

### 1. Launch the AWS Cloud9 IDE
Click Start Lab at the top of these instructions. Wait for the status to say Ready, then close the panel.

Click AWS to open the Management Console (be sure to allow pop-ups).

Go to Services > Cloud9, find the reStart-python-cloud9 card, and click Open IDE.

Note: If prompted, select Discard for setting changes and No for third-party content.

<img width="700" height="300" alt="Lab 108_5" src="https://github.com/user-attachments/assets/02305571-8042-4805-ba3d-228f8a7282df" />

### 2. Set Up Your Python File
Go to File > New From Template > Python File.

Clear the file: Delete any sample code currently in the template.

Go to File > Save As..., name it hello-world.py, and save it in the /home/ec2-user/environment directory.

<img width="500" height="600" alt="Lab 108_1" src="https://github.com/user-attachments/assets/4d9fe76d-1c85-4c42-a883-5a212f2ead27" />


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

<img width="446" height="125" alt="Lab 108_3" src="https://github.com/user-attachments/assets/e18a893f-4a17-4e40-9162-17c0891a4847" />


Click the Run (Play) button at the top of the window.

Look at the bottom pane to confirm it printed: Hello, World

<img width="458" height="187" alt="Lab 108_4" src="https://github.com/user-attachments/assets/d80287e4-33ad-462e-9544-d68df33c51fb" />


Great job! I’ve officially written your first Python program.
