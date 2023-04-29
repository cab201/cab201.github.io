---
layout: default
title: Week 9 - Polymorphism
nav_order: 7
parent: Weekly Practicals
permalink: /practicals/week-9
---

# Worksheet 9: Polymorphism
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Read the Cheatsheet](../weekly-content/week-8){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .important-title }
> Download the Source Code
> 
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-09/archive/23se1-tue-9.zip){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-09/archive/23se1-wed-9.zip){: .btn .btn-purple .mr-2 }

---

# Worksheet 9: Polymorphism

This week we are going to be looking at polymorphism. We will between by looking at the general case of polymorphism and them looking at abstract class and interfaces.

# Polymorphism

1. Create an Auto namespace and an **Automobile** class. The class should hold fields for number of kilometres driven, make, year and price which are passed as parameters. Create a _Drive_ method that will add an integer to the overall number of kilometres driven. Override the _ToString_ method so that it outputs the details of the class.

    Create a **FinancedAutomobile** class that extends the Automobile class and also holds fields for the number of finances and rate. Override the _ToString_ method so that prints out all of the FinancedAutomobile fields.

    Create a TestAutomobile class. In the TestAutomobile create an Automobile array and store multiple Automobile and FinancedAutomobile objects. Create two loops that go through each of the classes and calls drive and another loop that goes through and prints out all the details.

1. Create a namespace **Library**. Create a class named **Book** that includes fields for title, author and price. Create two child classes, one named **Textbook** that includes a grade level and one called **CoffeeTable** book with contains a string of its image of its front page.

    Override the _ToString_ method in each of the classes which outputs each of the details.

    Create a **TestBook** class and a collection that that can hold Book, TextBook and CoffeeTable. Make sure that there are enough examples to test out all of your classes.

# Abstract

1. Create a project called Geometric. It should contain:

     1. An abstract class called GeometricPrism. It should include a height, a width and a length. The constructor should provide parameters for the height, width and length.
     2. An abstract GetVolume method.
     3. A Cuboid which is a GeometricPrism whose volume is determined by multiplying the height, width and length.
     4. A TriangularPrism is a GeometricPrism whose volume is determined by multiplying the height by half of the width and the length.

Write a TestPrism class which tests the construction and volumes.

1. Create a project called Sales. It should contain an abstract **SalesPerson** class that contains the both the first and last names. Create a constructor that contains both of these fields and properties to access them. Create a field called sale amount which will be set to zero. Create a _ToString_ method that returns both first, last and the sales amount. Create an abstract method that will add a sale value to the sale amount.

    Create a **RealEstateSalesPerson** class. Its constructor should contain a field for a commission rate. It should override the add sale method that accepts a value of a house price, which is used to calculate the commission.

    Create a **Scout** class which should inherit SalesPerson. Its constructor should take the value for the price of a cookie box. It should override the add sale method that to accept a number of cookie boxes sold.

    Create a **TestSales** class. It should create an of both SalesPerson classes. Test out the add sale method and print out the results.

# Interfaces

1. Create a namespace called **Conversion**. In it create an interface called **IConverter.** It contains a single method called **Convert** which accepts and return a double.

    Create four classes called CentimetresToMeters, CelsiusToFahrenheit, KilometersToMiles and DegreesToRadians. Make each of the classes implement IConverter, and in particular make sure that they use the Convert method using the formulas listed below.

        1. Centimetres = Metres / 100
        2. Fahrenheit = (Celsius \* 9 / 5) + 32
        3. Kilometres = Miles \* 1.609344
        4. Radians = Degrees \* Math.PI / 180

    Write a TestConvert program that creates each of the 4 objects created and calls their Convert methods.

1. Create a namespace called **Arithmetic**. Create an **IArithmetic** interface with a _Perform_method. The Perform method should contain 2 number and return another number. Create the following classes: **Add** , **Subtract** , **Multiply** and **Divide** , all of which will implement IArithmetic with an appropriate method.

    Finally, write a program called **TestArithmetic**. It should test each of the classes.