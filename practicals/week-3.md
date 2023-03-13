---
layout: default
title: Week 3 - Collections
nav_order: 1
parent: Weekly Practicals
permalink: /practicals/week-3
---

# Worksheet 3: Collections
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Read the Cheatsheet](../weekly-content/week-3){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .important-title }
> Download the Source Code
> 
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-03/zipball/23se1-tue-9){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-03/zipball/23se1-wed-9){: .btn .btn-purple .mr-2 }

---

This week we are looking at Collections, in particular the array and List. We learnt that arrays can be single or multidimensional, and they can have methods. We then looked at List, which are like arrays but have a variable length, and Dictionaries, which work as associative arrays. Have a look at this week's summary before continuing.

# Accessing and Searching Arrays

1. Write a program called **ArrayDouble** which stores an array of 5 doubles and prints them out. The numbers in the array should be hard coded. You should use an array and a for loop.

1. Write a program called **ArrayIntegerLimit.** This should accept a limit from the user. The program should then accept a set of integers, up to the limit. When the program has finished it should

     1. Show each of the integers
     2. Display the total
     3. Display the average.

2. Write a program called **CheckPostcodes**. It should contain 10 postcodes which are hardcoded. It should then accept a value from the user which and either print out "Success" if the post code is found or respond with "Error" if it is not.

# Array Methods

1. Write a program called **ArrayDoubleSort**. It should accept 10 doubles which are unsorted. It should run Array.Sort to sort the values and print out the sorted array. It should then output the sorted array using a ForEach loop.

1. Write a program called **NameSort**. It should ask the user for the number of names. It should then ask the user to enter each of the names. You should call Array.Sort to sort the names. It should then output the sorted array using a ForEach loop.

# Lists

1. Write a program called **ListFive**. Store 5 integers into a List and then print them out. You are to hardcode all of the values.

1. Write a program called **ListLimit**. This should accept a limit from the user. The program should then accept a set of integers, up to the limit. When the program has finished it should:

     1. Show each of the integers
     2. Display the total
     3. Display the and the average.

2. Write a program called **RemoveList**. You are to use a List and a number of loops. The program should do the following steps:

      1. Get a list of numbers from the user.
      2. While there are still items in the list

          1. Print out the list of number
          2. Ask the user which number that would like removed
          3. Remove the number

    The program should continue until all the number are removed.

# Dictionaries

1. Write a program called **International**. The program will contain a Dictionary with the following countries and their international express fees. You are to hard code all of the values. Your program should then read a country name with Console.ReadLine() and then print out that country's express fee.

    | **Country** | **Fee** |
    | --- | --- |
    | UK | 100 |
    | USA | 300 |
    | France | 200 |
    | Chile | 500 |
    | China | 1000 |
    | Egypt | 600 |


2. Write a program called **Postcode**. The program will contain a Dictionary with the following cities and their postcodes. You are to hard code all of the values. Your program should then read a postcode with Console.ReadLine() and then print out the city it belongs to.

    | **Code** | **City** |
    | --- | --- |
    | 2000 | Sydney |
    | 2600 | Canberra|
    | 3000 | Melbourne |
    | 4000 | Brisbane |
    | 5000 | Adelaide |
    | 6000 | Perth |
    | 7000 | Hobart |
    | 0800 | Darwin |


3. Write a program called **PhoneRates**. The program will contain a Dictionary with the following area codes and their rates. You are to hard code all of the values. Your program should then read an area code with Console.ReadLine() and then print out the rate associated with it.

    | **Area Code** | **Rate** |
    | --- | --- |
    | 100 | 0.70 |
    | 200 | 0.10 |
    | 300 | 0.05 |
    | 400 | 0.16 |
    | 500 | 0.24 |
    | 600 | 0.30 |

# GradeScope Exercises

Go to this week's GradeScope exercises ([https://canvas.qut.edu.au/courses/2646/pages/2-dot-x-programming-exercises](https://canvas.qut.edu.au/courses/2646/pages/2-dot-x-programming-exercises)) to test your knowledge about collections.

# Homework

1. Write a program called **ArrayInteger** which stores an array of 5 integers and prints out their total. The numbers in the array should be hard coded. You should use an array and a for loop.

1. Write a program called **IntegerReverse**. It should ask the user for the number of integers. It should then ask the user to enter each of the integers. You should call Array.Reverse to place the integers in reverse order that they were given. It should then output the reverse integers in the array. Try and use a foreach loop when presenting the results.

1. Write a program called **Workday**. The aim of the program is print out users' activities and how much time they take in a day. The program should ask the user what is the number of activities. Then it should ask the user for the name and the number of hours. Go through the list and calculate the percentage of time devoted to the task. If the number of hours is more than 24 then it should report an error. If the number of hours is less than 24 then it should store the hours as a missing element. Try the program with activities that equal less down, equal to and greater than 24 hours. An example is presented below.

    | **Task** | **Hours** | **Percentage** |
    | --- | --- | --- |
    | Work | 7 | 0.291667 |
    | Programming | 2 | 0.083333 |
    | Eat | 1 | 0.041667 |
    | Commute | 2 | 0.083333 |
    | Play Game | 1 | 0.041667 |
    | Sleep | 7 | 0.291667 |
    | Study | 2 | 0.083333 |
    | Missing | 2 | 0.083333 |

1. Write a program called **WorkshopAttendance**. It should contain two lists about workshop participants. The first list should contain the number of people at each workshop. The second list should contain the total number of people allowed at a workshop. Ask the user how many workshops there are and then go through and ask for the lists. Print out each of the lists. If the use enters a number of people greater than the number of people allowed then it should produce an error.