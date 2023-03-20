---
layout: default
title: Week 4 - Methods
nav_order: 2
parent: Weekly Practicals
permalink: /practicals/week-4
---

# Worksheet 4: Methods
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Read the Cheatsheet](../weekly-content/week-4){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .important-title }
> Download the Source Code
> 
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-04/archive/23se1-tue-9.zip){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-04/archive/23se1-wed-9.zip){: .btn .btn-purple .mr-2 }

---

This week we are looking at methods. Methods are one of the most important aspects of any programming language. This week we will look at various ways that you can use methods, such as learning about the syntax and semantics, learning about the value and reference types and then return types.

# Method Syntax and Semantics

1. Create a program called **TheAnswer** with a method called **TheQuestion**. TheQuestion should print out the number 42. You should call TheQuestion from TheAnswer Main method.

1. Create a program called **FortuneTeller** than contains a method called **MyFortune**. You should call MyFortune from Main. MyFortune should return a string consisting of the phrase "I see a tall, dark stranger in your future".

1. Write a program called **Convert** which contains a method called **ConvertKilometresToMiles.** The Main method should ask the user for a double representing a number of kilometres. It would then call ConvertKilometresToMiles. The ConvertKilometresToMiles method should take the kilometres and then convert it to miles. It should then return the miles. Remember that a mile is 1.60934 kilometres.

1. Create a program called **Average** with a method called **AverageArray**. AverageArray should accept an array and then return the average. AverageArray should be called from the main method. The array can be hard coded.

# Value and Reference Types

1. Create a program called **SortMyArray** with a method called **MySort**. Sort should accept an array of integers which is unsorted. Print out the array. Sort then sorts the array and returns it. Then you should print it out again. Sort should be called from Main, and its array of integers can be hard coded.

1. Create a program called **ToLowercase** with a method called **ToLower**. The program should accept an array of strings in multiple cases and return **void**. ToLower is to go through the array and transform each of strings to lower case. ToLower is to be called from and displayed from Main. The strings can be hard coded.

1. Create a program called **IntegerUtils**. It should have 3 methods which accept an array of integers and an integer. The three methods are:

     1. FindFirst, which finds the first instance of the integer in the array;
     2. FindLast which finds the last instance of the integer in the array; and
     3. FindAll which will find all of the instances of the integer in the array.

The first two methods should return an integer and the third method should return a list. All methods should come from the main menu. If there is no integer for the first two arrays it should return -1.

# Ref and Out

1. Write a program that contains a method **SwapValues** which takes in two integers as arguments and swaps their values. The method should use the ref keyword to modify the original variables passed in, rather than creating new variables.

1. Create a program called **TemperatureConversion** with a method called **Convert**. Convert should accept 3 parameters: Celsius, Fahrenheit and Kelvin. You will supply the Celsius parameter and the Fahrenheit and Kelvin will be returned to you. You are to call the method from main and display the results. Remember the following things about temperature conversion.

    Kelvin = Celsius + 273

    Fahrenheit = Celsius \* 9.0 / 5 + 32

1. Create a program called **Triangle** with a method called **GetTriangleDetails**. GetTriangleDetails should accept the side and height of an equilateral triangle and return the perimeter and the area. You are to call the method from main and display the results. Remember the following things about triangles.

    Perimeter = Side + Side + Side

    Area = Side \* Height / 2

# Putting it All Together

1. Create a program called **PaintingEstimate** which will estimate the cost of painting. PaintingEstimate should contain three methods.

     1. A method called **GetInputs** , which will accept three doubles which represent a room's width, length and height. You should assume that the room is rectangular and has four walls. All three values are to be entered by the user.
     2. A method called **PaintRoom** , which will determine the cost to paint a room considering that the cost per is $10/meter squared.
     3. A method called **OutputPainting** , which will output the cost of the painting.

    These methods should be called from the Main method.

2. Create a program called **MenuMathsUtils** which should allow users to sum, minus, multiply and divide two numbers. It should contain

    1. A called **MenuItems** that outputs a menu. It should accept an array that contains the following strings: 1. Sum, 2. Minus, 3. Multiplication, 4. Divide, 5. Quit. The MenuItems should then return the appropriate integer.
    2. A method called **EnterNumbers** which will allow the user the user to enter in two numbers.
    3. Methods called **Sum, Minus, Multiply** and **Divide**.
    4. A method called **Output** which will out output the answer.

# Homework

1. Write a program called **Memo**. It should contain a method called **MemoHeader** which should print out a string that says "C# Software Developer". You should call MemoHeader from Memo's Main method.

1. Create a program called **University** and a method called **Administration**. The Administration method should be called from the main method. The Administration method should accept a high school grade point average. If the grade point average is greater than or equal to 69.5 it should return 'Accepted', otherwise it should return 'Rejected'. The grade point average should be user inputted.

1. Create a program called **Library** and a method called **LibraryFine**. LibraryFine should accept an array of integers representing overdue library books. If the library book is over by 10 days or less then the fine is $5. If the library book is greater than 10 days overdue the fine will be $10. LibraryFine should go through the array and return the result. The array can be hardcoded.

1. Create a program called **Circle** with a method called **GetCircleDetails**. GetCircleDetails should accept a radius and return the diameter, perimeter and the area. You are to call the method from main and display the results. Remember the following things about circle.

    Diameter = 2 \* radius

    Circumference = 2 \* Math.PI \* radius

    Area = Math.PI \* radius \* radius

1. You are to write a program called **Friends**. You are to:

     1. Write a method that asks the user for a set of friends and returns it to them.
     2. Write a method that prints out all of the friends for each person.
     3. Write a method that says which of the users has the most friends.

    All of the methods should be called from the Main method.