---
layout: default
title: Week 5 - Streams
nav_order: 3
parent: Weekly Practicals
permalink: /practicals/week-5
---

# Worksheet 5: Streams
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Read the Cheatsheet](../weekly-content/week-5){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .important-title }
> Download the Source Code
> 
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-05/archive/23se1-tue-9.zip){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-05/archive/23se1-wed-9.zip){: .btn .btn-purple .mr-2 }

---

This week we are looking at streams to read and write files.

# CAB201 Programming Principles

# Worksheet 5: Streams

This week we are looking at streams. Streams are an alternative method of inputting and outputting data. You would already have seen one stream, the console, however, this week we are looking at other streams, mainly files.

Note that is this example you are requested to add methods. For most questions you don't need to add them. However, it will be beneficial for the rest of the semester.

# Directories and File I/O

1. Create an application called **FileCheck** which should check if a file exists. It should contain a method that ask for the filename from the user. Another method should then check if the file exists. If it does then it should output the time it was created, last written and accessed. If the file does not exist, then it should print out an error message. The Main method should just call the other two methods.

1. Create an application called **DirectoryCheck** which should check if a directory exists. It should contain a method that asks for the directory name from the user. Another method should display the fact that the file exists, and outputs its creation time, the last time that the directory was written to, the number of subdirectories and the number of files. If the directory does not exist, then the method should print out an error message. The Main method should just call the other two methods.

# Reading and Writing Text Files

1. Create an application called **FileOpen**. It should contain two methods. The first method should ask for the filename from the user. The second method should check if a file exists and output its data. You should attempt to see if the file works using the files "ShoppingList.txt" and "TheFiddlerOfDooney.txt". You should download the files from Canvas.

1. Create an application called **FileString**. The application should include a method that outputs to "output.txt". The method should output the following paragraph "In fairy-tales, witches always wear silly black hats and black coats, and they ride on broomsticks. But this is not a fairy-tale. This is about REAL WITCHES."

1. Create an application called **FileWrite**. It should contain 2 methods. The first method should ask for a filename. The second method should then read a sentence from the user and then output the sentence to a file. The method should continue to read in and write to a file until "999" is entered. The final "999" should not be entered in the file.

1. Create an application called **ReadEmployee**. It should have a method that read in the name of file. You may use "EmployeeDetails.txt" from Canvas as your file. Next, you should have a method that reads in the file, the average salary, the minimum salary and the maximum salary. The method should open the file and read in three items, an integer called employee id, a string containing the name and a double containing the salary. The items are delimitated by a comma. The method should read in the file and calculate the average, minimum and maximum salary. You should then write a final method that displays the results.

# Homework

1. Create an application called **SalesForce**. It should contain a method that enables you to write filename. Another method should read in the data from the file and print it out. You can use the file "Sales.txt" from Canvas. Once displayed it should look like the following:

        | Phil | Joe | Jenny |
        | --- | --- | --- |
        | 30 | 25 | 32 |
        | 41 | 10 | 34 |
        | 13 | 32 | 7 |
        | 24 | 20 | 25 |

1. Create an application called **WriteStudent**. It should contain a method that asks for a filename. Then write a method that asks for a student's number, name, GPA and their year in university, which should then be written to a file. You should continue to enter in student's details until the user indicates that they want to stop.

1. You are to create an application called **ArrayApplication**. It should contain a Main method which will call the following methods:

        1. A method called ArrayDetails. It should ask the user for a number to be the dimension of the array. It should then create the array.
        2. A method called EnterArray. It should accept the array as a parameter. It should then fill the array with integers.
        3. A method called DisplayArray. It should display the contents of the array.
        4. A method called EnterFilename. It should ask the user a filename and return it.
        5. A method called PrintArray. It should accept the array and a filename. It should print out the array to the filename.