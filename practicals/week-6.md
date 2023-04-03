---
layout: default
title: Week 6 - Classes
nav_order: 4
parent: Weekly Practicals
permalink: /practicals/week-6
---

# Worksheet 6: Classes
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Read the Cheatsheet](../weekly-content/week-6){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .important-title }
> Download the Source Code
> 
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-06/archive/23se1-tue-9.zip){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-06/archive/23se1-wed-9.zip){: .btn .btn-purple .mr-2 }

---

This week we are looking at classes. Classes are one of fundamental aspects of object-orientated programming. Without them you will struggle to formulated object-orientated programs. In this workshop you will work through classes, adding fields and methods, adding constructors, overloading your methods, visibility and a has-a relationship.

# Classes, Fields and Methods

1. Create a class called **WhoLivesHere**. The WhoLives class should contain 2 strings: a person and a city. Write a number of class initialisations (aka objects) to test that WhoLivesHere is working correctly.

1. Create a class called **SoccerPlayer**. The SoccerPlayer class contains properties that hold a player's name (string), jersey number (integer), goals scored (an integer) and assists (an integer). Write a number of class initialisations to test that the SoccerPlayer is working.

# Constructors

1. Create a set of classes based upon what you wrote for the previous exercises (WhoLivesHere, SoccerPlayer) , however, this time add a Constructor to each of them. Test that the constructor is working.

# Overloading

1. Create a class named **Car**. The Car should contain two fields, a model and a litre per kilometres. It should contain two constructors. One requires both fields to be filled and the second accepts the model and sets the litre to kilometre to be 50. Test that Car is working by writing a method that displays each of the fields.

1. Create a class named **SalesTransaction**. The SalesTransaction contains fields for a salesperson name, sales amount and commission and a field that stores the commission rate. It contains two constructors. One constructor accepts values for the name, sales amount, and rate. It sets the commission as the sales times the commission rate. A second constructor sets accepts a name and sales amount, but sets the commission rate and the commission to 0. Test your example by using both constructors and displaying each of the fields.

# Visibility

1. Create a class called **HousePlant**. The HousePlant should have fields for the name (e.g. Philodendron), a price (e.g. $29.99) and if it has been fed in the past month (e.g. true). Create properties that allow for the **get** and **set** accessors for each field. Demonstrate that the class works.

1. Create a class called **Student**. It should take two fields, student and number. The two fields should have **get** accessors and private **set** methods. Demonstrate that the class works.

# Has-A Relationship

1. Create a class called **Number**. Its constructor should take in an integer as a parameter. It should then have two additional fields square (n2) and cube (n3). The number should have a **get** and **set** accessor, while the square and cube should have a get assessor. The set accessor for number should set the square and cube values. Create a class called **TestNumber**. Create a number and test out all of its properties. Change the number and then test it out again.

1. Create a class called **Circle** with fields named: radius, area and dimeter. Circle should take radius in its constructor. The radius should have **get** and **set** accessors while the area and diameter should have **get** accessors. The radius set accessor should also set the area and the diameter. Create a class called **TestCircle** which will call the Circle. Use **TestCircle** to create three Circle objects. Display all of the Circle's properties. Then change each of the Circle's sizes and display the properties again. Make sure that you showcase the area and dimeter to two decimal places.

# Homework

1. Create a class named **Pizza**. The Pizza class should contain a set of toppings (a string), a diameter (integer) and a price (double). Add a constructor which will accept the parameters. Write a DisplayPizza which will print out all of the details. Write a number of class initialisations to test that the Pizza is working.

1. Create a class called **Scout**. It contains fields for the name, troop number and dues owed. Include 2 overloaded constructors. One that allows you to set the name and troop number with a dues owed value of 0 and one that lets you set all of the fields. You should test it out by instating 2 Scout classes and displaying their fields.

1. Create a class called **ClassifiedAd**. ClassifiedAd should include fields for the category (e.g. Used Cars), the number of words and the price. Include properties that contain a **get** and a **set** accessors for the category and the number of words, but only a **get** accessor for the price. The price is calculated at 11 cents per word. Demonstrate that the class works.

1. Create a class called **DayType**. It should implement the days of the week. It should accept an integer (e.g. 0) and then transform it to a day of the week (e.g. Sun). The class should be able to perform the following operations:

     1. Set the day
     2. Print the day
     3. Return the day
     4. Return the next day
     5. Return the previous day
     6. Calculate and return the day by adding certain days to the current day. For example, if the current day is Monday and we add 4 days, the day to be returned is Friday. Similarly, if today is Tuesday and we add 13 days, the day to be returned is Monday.

Create a class called **TestDayType**. It will create a DayType and then test each of the operations.
