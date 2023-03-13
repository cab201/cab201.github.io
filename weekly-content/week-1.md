---
layout: default
title: Week 1 - Expressions
nav_order: 2
permalink: /weekly-content/week-1
---

# Week 1 - Expressions
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

In this topic, we will learn about the basic building blocks of C# programs, which are types, expressions, and variables.

## Expressions

An expression is a combination of values, variables, operators, and method calls that are evaluated to produce a single value.

```csharp
// This is an expression
int x = 5 + 3;

// Evaluate the type of the expression
Console.WriteLine(x.GetType());
// Output: System.Int32
```

## Variables

A variable is a named storage location that can hold a value of a particular type.

```csharp
// Declare a variable
int x;

// Assign a value to the variable
x = 5;

// Display the value of the variable
Console.WriteLine(x);
```

Common variable types:

| Type | Description |
| --- | --- |
| `int` | A 32-bit signed integer |
| `double` | A double-precision floating point number |
| `char` | A single 16-bit Unicode character |
| `string` | A sequence of Unicode characters |
| `bool` | A Boolean value |

## Strings

A string is a sequence of Unicode characters.

```csharp
// Declare a string
string name = "Dan";

// Concatenate strings
string greeting = "Hello " + name;

// Interpolate strings
string greeting = $"Hello {name}";

// String formatting
string greeting = string.Format("Hello {0}", name);

// String methods

// 1. Length: Returns the length of the string
Console.WriteLine(name.Length);

// 2. ToUpper: Returns the string in uppercase
Console.WriteLine(name.ToUpper());

// 3. ToLower: Returns the string in lowercase
Console.WriteLine(name.ToLower());

// 4. Contains: Returns true if the string contains the specified value
Console.WriteLine(name.Contains("o"));

// 5. StartsWith: Returns true if the string starts with the specified value
Console.WriteLine(name.StartsWith("J"));

// 6. EndsWith: Returns true if the string ends with the specified value
Console.WriteLine(name.EndsWith("n"));

// 7. IndexOf: Returns the index of the first occurrence of the specified value
Console.WriteLine(name.IndexOf("o"));

// 8. LastIndexOf: Returns the index of the last occurrence of the specified value
Console.WriteLine(name.Substring(1, 2));
```
For more information on strings, see [String Class](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-6.0).

## Type Conversion

Type conversion is the process of converting a value from one type to another. There are two types of type conversion:

- **Implicit conversion**: No data is lost in this conversion. The conversion is done automatically by the compiler.
- **Explicit conversion**: Data may be lost in this conversion. The conversion must be explicitly requested by the programmer using a cast operator.

Example of implicit conversion:

```csharp
int x = 5;
double y = x;
```

Example of explicit conversion:

```csharp
double x = 5.5;
int y = (int)x;

// By doing this, we lose the decimal part of the number
```

## User Input and Output

### Console Input

To read input from the console, we use the `Console.ReadLine()` method. This method returns a string.

```csharp
string name = Console.ReadLine();
```

### Console Output

To write output to the console, we use the `Console.WriteLine()` method.

```csharp
Console.WriteLine("Hello World!");
```