# Working with the String Data Type

In Python, a collection of letters and symbols is called a string. Strings are used extensively for handling input and output.

## Objectives
Write Python code using the string data type

Concatenate strings

Use the string to get user input

Format strings for output

Estimated completion time: 45 minutes

## Setup Instructions
1. Accessing the AWS Cloud9 IDE
Start your lab environment by choosing Start Lab.

Wait until you see the message Lab status: ready, then close the panel.

Choose AWS to open the Management Console in a new browser tab.

In the Console, navigate to Services > Cloud9.

Locate the reStart-python-cloud9 card and choose Open IDE.

2. Creating your Python exercise file
From the menu bar, choose File > New From Template > Python File.

Delete the sample code provided from the template file.

Choose File > Save As... and name the file string-data-type.py.

Save it under the /home/ec2-user/environment directory.

3. Accessing the terminal session
In your IDE, choose the + icon and select New Terminal.

To display the present working directory, enter pwd. This should point to /home/ec2-user/environment.

### Exercise 1: Introducing the string data type

A text file containing a logical sequence of commands is a script.

From the navigation pane of the IDE, choose the .py file you created.

In the file, enter the following code:

Python
myString = "This is a string."
print(myString)
Save and Run the file.

Extend the script by using the built-in function type() to get the data type. Enter the following code:

Python
print(type(myString))
print(myString + " is of the data type " + str(type(myString)))
Save and Run the file again.

<img width="450" height="355" alt="Lab 110_1" src="https://github.com/user-attachments/assets/068b9a03-7d32-4ac3-b9f2-079b7a02250e" />


### Exercise 2: Working with string concatenation

String concatenation is the process of combining two strings into one using the plus sign (+).

Return to the Python script.

Create two strings and concatenate them by entering the following code:

Python

firstString = "water"

secondString = "fall"

thirdString = firstString + secondString

print(thirdString)

Save and Run the file.

<img width="367" height="244" alt="Lab 110_2" src="https://github.com/user-attachments/assets/72108af3-758d-4cde-8424-2213cf6b1a4f" />


### Exercise 3: Working with input strings
Information that a user enters is known as input. The input() function pauses the code until a user enters a string and presses ENTER.

Return to the Python script and enter the following code:

Python

name = input("What is your name? ")

print(name)

Save and Run the file.


When prompted in the terminal, enter a name and press ENTER.

<img width="450" height="355" alt="Lab 110_1" src="https://github.com/user-attachments/assets/068b9a03-7d32-4ac3-b9f2-079b7a02250e" />


### Exercise 4: Formatting output strings

When your script communicates information back to the user, it is called output. You will create a survey and output the collected information using the format() function.

Return to the Python script and enter the following code:

Python

color = input("What is your favorite color?  ")

animal = input("What is your favorite animal?  ")

Use the print() function with multiple variables to format a string:


Python

print("{}, you like a {} {}!".format(name, color, animal))

Save and Run the file.

The Python shell will wait for your input. Enter a name, a color, and an animal as prompted.

Confirm that the script prints the formatted string using the three pieces of information provided.
<img width="470" height="215" alt="Lab 110_5" src="https://github.com/user-attachments/assets/150d6d73-2380-47cf-a9dd-3122dedc15fe" />


Note: The final print() statement uses the format() function, where the braces ({}) act as placeholders for the variables passed into the function's parentheses.

<img width="568" height="448" alt="Lab 110_4" src="https://github.com/user-attachments/assets/a6a3a443-0bbe-4150-9619-ea65d9c853cc" />

