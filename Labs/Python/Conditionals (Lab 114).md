# Working with Conditionals

Lab Overview
A section of code that compares two pieces of information is called a conditional statement. You can use conditionals to create different paths through a program. Using comparative operators, you will write a program that makes decisions.

## Objectives
Use the if statement

Use the else statement

Use the elif statement

Estimated completion time: 45 minutes

## Setup Instructions

1. Accessing the AWS Cloud9 IDE
Start your lab environment by choosing Start Lab.

Wait until the message Lab status: ready appears, then close the panel.

Choose AWS to open the Management Console.

Navigate to Services > Cloud9 and choose Open IDE on your environment card.


2. Creating your Python exercise file
   
From the menu bar, choose File > New From Template > Python File.

Delete the sample code provided.

Choose File > Save As..., name the file conditionals.py, and save it under the /home/ec2-user/environment directory.


3. Accessing the terminal session
   
In the IDE, choose the + icon and select New Terminal.

Enter pwd to confirm you are in the correct directory.

### Exercise 1: Working with the if statement
In this exercise, you will edit a Python script to ship packages.

From the navigation pane, open conditionals.py.

Use the input() function to get information from the user:

Python

userReply = input("Do you need to ship a package? (Enter yes or no) ")
Use the if statement to print a response. Note that Python uses indentation (one tab) to define logic blocks:

Python
if userReply == "yes":
    print("We can help you ship that package!")
Note: The == symbol is a comparative operator meaning "is equal to".

Save and Run the file.

At the prompt, enter yes and confirm the response.

Run the file again, enter no, and confirm the program exits with no display.

Screenshots:
[Insert Screenshot of If Statement Output Here]

### Exercise 2: Working with the else statement
In this exercise, you will improve the script by providing a reply even if the user does not want to ship a package.

Add the else statement to handle the "no" condition:

Python
else:
    print("Please come back when you need to ship a package. Thank you.")
Save and Run the file.

Test both yes and no inputs to confirm the program provides the correct response for each.

Screenshots:
[Insert Screenshot of Else Statement Output Here]

### Exercise 3: Working with the elif statement
Improve the script by offering additional services using the elif (else-if) statement.

In the Python script, enter the following code:

Python

userReply = input("Would you like to buy stamps, buy an envelope, or make a copy? (Enter stamps, envelope, or copy) ")

if userReply == "stamps":
    print("We have many stamp designs to choose from.")
elif userReply == "envelope":
    print("We have many envelope sizes to choose from.")
elif userReply == "copy":
    copies = input("How many copies would you like? (Enter a number) ")
    print("Here are {} copies.".format(copies))
else:
    print("Thank you, please come again.")
Save and Run the file.

Test the program multiple times with the following inputs:

stamps

envelope

copy (followed by a number)

Any other text to trigger the else statement.

Note: The if, elif, and else statements allow only one path to run at a time. The program stops checking other conditions once it finds a match.

Screenshots:
[Insert Screenshot of Elif Statement Operations Here]

## Conclusions:  I have written a Python script that successfully uses decision-making logic with if, elif, and else statements.
