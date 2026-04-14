# Working with Lists, Tuples, and Dictionaries

In Python, string and numeric data types are often used in groups called collections. This lab explores three primary collections supported by Python: the list, the tuple, and the dictionary.

## Objectives
Use the list data type

Use the tuple data type

Use the dictionary data type

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

Choose File > Save As..., name the file collections.py, and save it under the /home/ec2-user/environment directory.

3. Accessing the terminal session
In the IDE, choose the + icon and select New Terminal.

Enter pwd to confirm you are in the correct directory.

### Exercise 1: Introducing the list data type
Defining a list
From the navigation pane, open collections.py.

Enter the following code:

Python
myFruitList = ["apple", "banana", "cherry"]

print(myFruitList)

print(type(myFruitList))

Save and run the file.

Accessing a list by position
In programming, list positions start at zero (0). To access items by position, enter the following code:

Python

print(myFruitList[0])

print(myFruitList[1])

print(myFruitList[2])

Save and run the file.

Changing the values in a list
To change "cherry" to "orange" at the third position (index 2), enter:

Python

myFruitList[2] = "orange"

print(myFruitList)

Save and run the file.

<img width="574" height="277" alt="Lab 111_1" src="https://github.com/user-attachments/assets/d9df99af-3ae8-43c9-9463-a619c495bef8" />


### Exercise 2: Introducing the tuple data type
Defining a tuple
The tuple is like a list, but it is immutable (cannot be changed). It uses parentheses () instead of brackets [].

Create a tuple by entering the following code:

Python

myFinalAnswerTuple = ("apple", "banana", "pineapple")

print(myFinalAnswerTuple)

print(type(myFinalAnswerTuple))

Save and run the file.

Accessing a tuple by position
Like a list, items are accessed by index:

Python

print(myFinalAnswerTuple[0])

print(myFinalAnswerTuple[1])

print(myFinalAnswerTuple[2])

Save and run the file.

<img width="577" height="261" alt="Lab 111_2" src="https://github.com/user-attachments/assets/a6386720-9a03-4091-a3ca-854c9a5b68f6" />

<img width="513" height="205" alt="Lab 111_3" src="https://github.com/user-attachments/assets/becc48bf-99eb-480e-b2f9-ea14824388bd" />

<img width="525" height="299" alt="Lab 111_4" src="https://github.com/user-attachments/assets/85f1308b-1182-4b30-86e7-aabf18baf180" />


### Exercise 3: Introducing the dictionary data type
Defining a dictionary
A dictionary is a list with named positions (keys).

Enter the following code to create a dictionary of favorite fruits:

Python

myFavoriteFruitDictionary = {
  "Akua" : "apple",
  "Saanvi" : "banana",
  "Paulo" : "pineapple"
}

print(myFavoriteFruitDictionary)

print(type(myFavoriteFruitDictionary))

Save and run the file.


Accessing a dictionary by name
Use the name (key) to access the specific value:

Python

print(myFavoriteFruitDictionary["Akua"])

print(myFavoriteFruitDictionary["Saanvi"])

print(myFavoriteFruitDictionary["Paulo"])

Save and run the file.

<img width="579" height="273" alt="Lab 111_6" src="https://github.com/user-attachments/assets/62c4b6f9-88c2-4095-ba78-176defb7006b" />


