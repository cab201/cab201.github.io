---
layout: default
title: Week 7 - Exceptions
nav_order: 5
parent: Weekly Practicals
permalink: /practicals/week-7
---

# Worksheet 7 - Exceptions
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
> [Tuesday Class (9-11am)](https://github.com/cab201/prac-07/archive/23se1-tue-9.zip){: .btn .btn-purple .mr-2 }
> [Wednesday Class (9-11am)](https://github.com/cab201/prac-07/archive/23se1-wed-9.zip){: .btn .btn-purple .mr-2 }

---

# Worksheet 7: Exceptions

This week we are looking at exceptions, a powerful tool that makes error handling in a complex system more manageable, and is practically a necessity in object-oriented programming.

# Who Lives Here

Download WhoLivesHere.zip – this contains a modified version of the WhoLivesHere class from Week 6. Modify the constructor to make it throw the following exceptions if invalid data is passed to it:

1. If null is passed to either the name or city fields, it must throw an ArgumentNullException
2. If an empty string is passed to either the name or city fields, it must throw an ArgumentException
3. If the age passed in is less than 0 or greater than 150, it must throw an ArgumentOutOfRangeException

# Contacts

Download Contacts.zip. Two classes are used to make a contacts application: Person and Contacts. Add the following exceptions to the appropriate methods:

1. The Person class must throw the following exceptions:
     1. Constructor:
        ArgumentNullException when either the name, phone number, or email are empty strings
2. The Contacts class must throw the following exceptions:
     1. addPerson():

        - ArgumentException when adding a person whose name is already in the list

     2. removePerson():

        - ArgumentOutOfRangeException when attempting to remove when the list is empty

     3. getPerson():

        - ArgumentException when attempt to retrieve a person who is not in the list

# ByteCalculator – Throwing Exceptions

Create a **ByteCalculator** class that takes an expression as a string and performs binary arithmetic operations on two Byte numbers. It has a string property called _Expression_, a constructor with a single string parameter that sets Expression, and a method called Evaluate (without any parameter) that returns the result of the expression.

In the Expression setter, ensure all the following conditions are met, if not, throw an ArgumentException, with a message of your choice to describe the non-compliance:

- The string must contain exactly one operator (+, -, \* or /).
- The string must contain exactly two operands, separated by the operator.
- The two numbers must be valid bytes (integers between 0 and 255)

In the Evaluate method, evaluate and return the result of the expression, throwing the following exceptions:

- DivideByZeroException, when the expression is a division, and the second operand is a zero.
- OverflowException, when the expression evaluates to a number less than 0, or more than 255.

Then test the ByteCalculator in the Main method and ensure the correct exceptions are thrown. If necessary, consult the following exceptional cases:

- InvalidArgumentException: No operator; more than one operator; invalid operand (non-numeric); invalid operand (negative number); invalid operand (overflow); invalid operand (non-integer).
- DivideByZeroException: Division by zero.
- OverflowException: Negative result; Overflow result.

_Note: Use integer division when evaluation a division. Each operand should be trimmed before being parsed to a byte._

# ByteCalculator - Catching Exceptions

Using the ByteCalculator and the test cases from the previous question, create a class called **ByteCalculatorTests** that has a private List of ByteCalculator. This class has an empty constructor that initialises the private List, a public AddTest method that takes a string and add a new ByteCalculator to the private list, and a RunTests method (without parameters) that evaluates all the ByteCalculator in the list.

Make sure that the RunTests method does not crash the program and can run all the tests, displaying the error message, if any, of each test in the console.