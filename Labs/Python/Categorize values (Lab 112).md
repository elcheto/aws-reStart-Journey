# Categorizing Values

In Python, you can mix different data types within a single list. This lab demonstrates how to create a list with various types and use a loop to process and print the values.

## Objectives
Use numeric data types

Use string data types

Use the list data type

Use a for loop

Use the print() function

Estimated completion time: 30 minutes

## Setup Instructions
1. Accessing the AWS Cloud9 IDE
Start your lab environment by choosing Start Lab at the top of the instructions.

Wait until you see the message Lab status: ready, then close the panel.

Choose AWS to open the Management Console in a new tab.

Navigate to Services > Cloud9.

In the Your environments panel, locate the reStart-python-cloud9 card and choose Open IDE.


2. Creating your Python exercise file
From the menu bar, choose File > New From Template > Python File.

Delete the sample code from the template file.

Choose File > Save As... and name the file categorize-values.py.

Save it under the /home/ec2-user/environment directory.


3. Accessing the terminal session
In the IDE, choose the + icon and select New Terminal.

Enter pwd to confirm your working directory is /home/ec2-user/environment.

Verify that your new .py file is located in this directory.

### Exercise 1: Creating a mixed-type list
You can mix data types in a Python list. In many other languages, this capability is not a feature of lists. In this exercise, I will explore this capability.

From the navigation pane, open the .py file you created in the previous section.

Define a list with different types by entering the following code:

Python
myMixedTypeList = [45, 290578, 1.02, True, "My dog is on the bed.", "45"]
Use a for loop statement to traverse the list and print the data type for each item:

Python

for item in myMixedTypeList:
    print("{} is of the data type {}".format(item,type(item)))
    
Save and Run the file.

<img width="506" height="317" alt="Lab 112_1" src="https://github.com/user-attachments/assets/949ee00f-90f0-4e7d-b601-1a5661f2a16c" />


Confirm that the script runs correctly and that the output displays as you expect.

<img width="457" height="174" alt="Lab 112_2" src="https://github.com/user-attachments/assets/2c6d9994-10bc-45df-a33a-feb46b9afef2" />


## Summary
This exercise reinforced the Python programming concepts covered in previous labs. Although the code consists of only a few lines, it demonstrates the power and flexibility of Python's list handling and iteration.
