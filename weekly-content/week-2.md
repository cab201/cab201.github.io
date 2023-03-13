---
layout: default
title: Week 2 - Structured Programming
nav_order: 3
permalink: /weekly-content/week-2
---

# Week 2 - Structured Programming
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

---

In this topic, we will learn about structured programming in C#. Structured programming is a programming paradigm that uses a sequence of statements to perform a task.

Structure programming involves the use of a code block, which is a sequence of statements enclosed in curly braces `{ }`.

```csharp
// This is a code block
{
    // This is a statement in the code block
    Console.WriteLine("Hello World!");
}
```

## Control Flow

### Boolean Expressions and Boolean Operators

A boolean expression is an expression that evaluates to a boolean value and can be chained together using boolean operators.

```csharp
int min = 0;
int max = 10;
int x = 5;

// Check if x is greater than min and less than max
bool result = x > min && x < max;

// Check if x is equal to min or max
result = x == min || x == max;

// Check if min and max are different
result = min != max;
```
Some common boolean operators are:

| Operator | Description |
| --- | --- |
| `&&` | Logical AND |
| `||` | Logical OR |
| `!` | Logical NOT |

### `if` Statements

An `if` statement is a control flow statement that allows the program to execute a block of code if a condition is true.

```csharp
// Usually, the condition involves a variable
int x = 5;
bool isPositive = x > 0;

// Check if x is greater than 0
if (isPositive)
{
    // This code block will be executed if x is greater than 0
    Console.WriteLine("x is greater than 0");
}
```

### `else` Statements and nested `if` Statements

An `else` statement is a control flow statement that allows the program to execute a block of code if a condition is false.

```csharp
int x = 5;

// Check if x is greater than 0. Notice that the condition is not stored in a variable this time.
if (x > 0)
{
    // This code block will be executed if x is greater than 0
    Console.WriteLine("x is greater than 0");
}
else
{
    // This code block will be executed if x is less than or equal to 0
    Console.WriteLine("x is less than or equal to 0");
}
```

An `else` statement can be used in conjunction with an `if` statement to create a nested `if` statement.

```csharp
int x = 5;

// Check if x is greater than 0
if (x > 0)
{
    // This code block will be executed if x is greater than 0
    Console.WriteLine("x is greater than 0");
}
else
{
    // Check if x is less than 0
    if (x < 0)
    {
        // This code block will be executed if x is less than 0
        Console.WriteLine("x is less than 0");
    }
    else
    {
        // This code block will be executed if x is equal to 0
        Console.WriteLine("x is equal to 0");
    }
}
```

### Cascading with `else if`

An `else if` statement is a control flow statement that allows the program to execute a block of code if a condition is `true`, and the previous conditions are `false`.

```csharp
int year = 2021;

// Check if year is a leap year. 
// A leap year is a year that is divisible by 4, but not by 100, unless it is also divisible by 400.
if (year % 4 == 0)
{
    Console.WriteLine("{0} is a leap year", year);
}
else if (year % 100 == 0)
{
    Console.WriteLine("{0} is not a leap year", year);
}
else if (year % 400 == 0)
{
    Console.WriteLine("{0} is a leap year", year);
}
else
{
    Console.WriteLine("{0} is not a leap year", year);
}
```

### `switch` Statements

A `switch` statement is a control flow statement that allows the program to execute a block of code based on the value of a variable.

```csharp
int gpa = 5;

// Returns a description of the GPA:
switch (gpa)
{
    case 7:
        Console.WriteLine("High Distinction");
        break;
    case 6:
        Console.WriteLine("Distinction");
        break;
    case 5:
        Console.WriteLine("Credit");
        break;
    case 4:
        Console.WriteLine("Pass");
        break;
    case 3:
    case 2:
    case 1:
        Console.WriteLine("Fail");
        break;
    default:
        Console.WriteLine("Invalid");
        break;
}
```
Use the `or` operator to combine multiple cases together instead of cascading `case` statements.

```csharp
int gpa = 5;

// Returns a description of the GPA:
switch (gpa)
{
    case 7:
        Console.WriteLine("High Distinction");
        break;
    case 6:
        Console.WriteLine("Distinction");
        break;
    case 5:
        Console.WriteLine("Credit");
        break;
    case 4:
        Console.WriteLine("Pass");
        break;
    case 3 or 2 or 1:
        Console.WriteLine("Fail");
        break;
    default:
        Console.WriteLine("Invalid");
        break;
}
```

## Loops

A loop is a control flow statement that allows the program to execute a block of code repeatedly.

### `while` Loops

A `while` loop is a control flow statement that allows the program to execute a block of code repeatedly while a condition is `true`.

```csharp
// Ask the user to enter a whole number until they enter a parsable number
Console.Write("Enter a whole number: ");
string input = Console.ReadLine();

while(!int.TryParse(input, out int number))
{
    Console.Write("Invalid input. Enter a whole number: ");
    input = Console.ReadLine();
}
```

### `do while` Loops

A `do while` loop is a control flow statement that allows the program to execute a block of code repeatedly while a condition is `true`. The difference between a `while` loop and a `do while` loop is that the `do while` loop will always execute the block of code at least once.

```csharp
// Ask the user to enter a whole number until they enter a parsable number
string input;
do
{
    Console.Write("Enter a whole number: ");
    input = Console.ReadLine();
} while (!int.TryParse(input, out int number));
```

### `for` Loops

A `for` loop is a control flow statement that allows the program to execute a block of code repeatedly for a specified number of times. There are three parts to a `for` loop, separated by semicolons:

1. The initialization part, which is executed once before the loop starts.
2. The condition part, which is executed repeatedly while the condition is `true`.
3. The update part, which is executed repeatedly after each iteration.

```csharp
// Print the numbers 1 to 10

// Initialization (int i = 1): set i to 1
// Condition (i <= 10): check if i is less than or equal to 10
// Update (i++): increment i by 1
for (int i = 1; i <= 10; i++)
{
    // The second part of the for loop is executed repeatedly while the condition is true
    Console.WriteLine(i);
}
```

Note that this is equivalent to the following `while` loop:

```csharp
int i = 1;
while (i <= 10)
{
    Console.WriteLine(i);
    i++;
}
```

### `foreach` Loops

A `foreach` loop is a control flow statement that allows the program to execute a block of code repeatedly for each element in a collection.

```csharp
string[] names = { "Jane", "Mary", "Dan" };

// Print each name in the array
foreach (string name in names)
{
    Console.WriteLine(name);
}
```

### `break` and `continue`

The `break` statement is a control flow statement that allows the program to exit any loop prematurely.

```csharp
// Print the numbers 1 to 10, but exit prematurely if i is equal to 5
for (int i = 1; i <= 10; i++)
{
    // Exit the loop if i is equal to 5
    if (i == 5)
    {
        break;
    }

    Console.WriteLine(i);
}
```

The `continue` statement is a control flow statement that allows the program to skip the rest of the current iteration of a loop.

```csharp
// Print the numbers 1 to 10, skipping 5
for (int i = 1; i <= 10; i++)
{
    // Skip the rest of the current iteration if i is equal to 5
    if (i == 5)
    {
        continue;
    }

    Console.WriteLine(i);
}
```