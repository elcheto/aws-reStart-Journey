### Working with Numeric Data Types in Python
## Lab Overview
Python is a popular language among data scientists for analyzing large amounts of data. In this lab, I will explore the basic data types used to store numeric values.

## Objectives
Use the Python shell

Use the "int" data type

Use the "float" data type

Use the "complex" data type

Use the "bool" data type


## Setup Instructions
1. Accessing the AWS Cloud9 IDE
Start your lab environment by choosing Start Lab.

Wait until the message Lab status: ready appears.

Choose AWS to open the Management Console in a new tab.

Navigate to Services > Cloud9.

Locate the reStart-python-cloud9 card and choose Open IDE.

2. Creating your Python exercise file
From the menu bar, choose File > New From Template > Python File.

Delete the sample code from the template file.

Choose File > Save As... and name the file numeric-data.py.

Save it under the /home/ec2-user/environment directory.

3. Accessing the terminal session
In the IDE, choose the + icon and select New Terminal.

Enter pwd to confirm your working directory is /home/ec2-user/environment.

# Exercise 1: Using the Python Shell
In the terminal tab, start the Python shell by entering: python3.

Adding: Enter 2 + 2 and press ENTER.

Subtracting: Enter 4 - 2 and press ENTER.

Multiplying: Enter 2 * 2 and press ENTER.

Dividing: Enter 4 / 2 and press ENTER.

Exiting: To exit the shell, enter quit().

<img width="700" height="400" alt="Lab 109_1" src="https://github.com/user-attachments/assets/3731bb86-578f-47b1-9f11-290e29666243" />

<img width="451" height="55" alt="Lab 109_3" src="https://github.com/user-attachments/assets/5736f58c-1286-4301-9918-ef00b0ad644e" />


# Exercise 2: Introducing the int Data Type
Open your numeric-data.py file.

Enter the following code:

Python
print("Python has three numeric types: int, float, and complex")
Save the file and choose Run.

Creating a variable: On a new line, enter the following code:

Python
myValue=1

print(myValue)

print(type(myValue))

print(str(myValue) + " is of the data type " + str(type(myValue)))

<img width="645" height="159" alt="Lab 109_4" src="https://github.com/user-attachments/assets/01739031-552b-455d-8b51-4e5765cae415" />

Save and Run the file.


<img width="600" height="315" alt="Lab 109_5" src="https://github.com/user-attachments/assets/8aaa03f4-40a3-4e22-9e54-1e09f2c86244" />

# Exercise 3: Introducing the float Data Type
Return to the Python file and on a new line, enter:

Python
myValue=3.14

print(myValue)

print(type(myValue))

print(str(myValue) + " is of the data type " + str(type(myValue)))

Save and Run the file.

<img width="600" height="301" alt="Lab 109_6" src="https://github.com/user-attachments/assets/12f619cb-1de7-47a9-8055-02443e1cf8bb" />


# Exercise 4: Introducing the complex Data Type
Return to the Python file and enter:

Python
myValue=5j

print(myValue)

print(type(myValue))

print(str(myValue) + " is of the data type " + str(type(myValue)))

Save and Run the file.

<img width="600" height="262" alt="Lab 109_7" src="https://github.com/user-attachments/assets/fbfaff8e-4f01-4229-81fd-2bb567734853" />


# Exercise 5: Introducing the bool Data Type
Return to your text file and enter:

Python
myValue=True
print(myValue)
print(type(myValue))
print(str(myValue) + " is of the data type " + str(type(myValue)))
Save and Run the file.

Return to the file and add the code for the False value:

Python
myValue=False

print(myValue)

print(type(myValue))

print(str(myValue) + " is of the data type " + str(type(myValue)))

Save and Run the file one last time.

<img width="487" height="407" alt="Lab 109_9" src="https://github.com/user-attachments/assets/53df6148-46a3-4c48-8476-41b7c78b86af" />

