---
layout: default
title: Week 4 - Methods
nav_order: 5
permalink: /weekly-content/week-4
---

# Week 4 - Collections
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-4){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about methods in C#. A method is a block of code that performs a specific task.

## Method Syntax and Semantics

### Method Declaration

A method is composed of a signature and a body. The signature of a method consists of the method name, the return type, and the parameters. The body of a method consists of the statements that are executed when the method is called.

```csharp
// Method signature
public static int Add(int firstNumber, int secondNUmber)
{
    // Method body
    return firstNumber + secondNumber;
}
```

In the method signature:
- `public` is the access modifier. It specifies the visibility of the method. In this case, the method is public, which means that it can be called from anywhere in the program. There are four access modifiers in C#: `public`, `private`, `protected`, and `internal`. We will learn more about access modifiers in a later topic.
- `static` is a keyword that specifies that the method is a static method. We will learn more about static and instance (non-static) methods in a later topic. Static methods are also called class methods, or functions in functional programming.
- `int` is the return type of the method. In this case, the method returns an integer. If the method does not return a value, the return type is `void`.
- `Add` is the name of the method. The name of a method should be a verb that describes what the method does.
- `(int firstNumber, int secondNumber)` is the list of parameters. A parameter is a variable that is passed to the method. In this case, the method takes two integer parameters, `firstNumber` and `secondNumber`.

### Method Call

A method is called by specifying the name of the method and passing the arguments to the method. The arguments are the values that are passed to the parameters of the method.

**Note:** The arguments must be passed in the same order as the parameters.

```csharp
// Call the Add method
int result = Add(1, 2);
Console.WriteLine(result);
// Output: 3
```

In the example above, the method `Add` is called with the arguments `1` and `2`. The arguments are passed to the parameters `firstNumber` and `secondNumber`, respectively. The method returns the value `3`, which is assigned to the variable `result`.

### Method Overloading

A method can have the same name as another method, as long as the signatures of the methods are different. This is called method overloading. For example, the method `Add` can be overloaded as follows:

```csharp
// Overloading with different number of parameters
public static int Add(int firstNumber, int secondNumber, int thirdNumber)
{
    return firstNumber + secondNumber + thirdNumber;
}

// Overloading with different parameter types
public static double Add(double firstNumber, double secondNumber)
{
    return firstNumber + secondNumber;
}

```

## Value and Reference Types

### Value Types

Value types are types that store the actual value. When a value type is assigned to a variable, the value is copied to the variable. For example, when an integer is assigned to a variable, the value of the integer is copied to the variable.

```csharp
int firstNumber = 1;
int secondNumber = firstNumber;
secondNumber = 2;
Console.WriteLine(firstNumber);
// Output: 1
```

In the example above, the value of `firstNumber` is copied to `secondNumber`. When `secondNumber` is assigned a new value, the value of `firstNumber` is not affected.

### Reference Types

Reference types are types that store a reference to the value. When a reference type is assigned to a variable, the reference is copied to the variable.

```csharp
int[] firstArray = new int[] { 1, 2, 3 };
int[] secondArray = firstArray;
secondArray[0] = 4;
Console.WriteLine(firstArray[0]);
// Output: 4
```

In the example above, the reference to `firstArray` is copied to `secondArray`. When `secondArray` is modified, the value of `firstArray` is also modified.

### Passing Parameters

When a value type is passed to a method, the value is copied to the parameter. For example, consider the following method that tries to modify the value of a parameter to `2`:

```csharp
// Method that modifies the value of a parameter
public static void ModifyValue(int value)
{
    value = 2;
}
```
  
When the method is called, the value of the argument is copied to the parameter. When the parameter is modified, the value of the argument is not affected.

```csharp
int number = 1;
ModifyValue(number);
Console.WriteLine(number);
// Output: 1
```

This is not the case for reference types. When a reference type is passed to a method, the reference is copied to the parameter. For example, consider the following method that tries to modify the first element of an array to `2`:

```csharp
// Method that modifies the value of a parameter
public static void ModifyValue(int[] value)
{
    value[0] = 2;
}
```

When the method is called, the reference to the argument is copied to the parameter. When the parameter is modified, the value of the argument is also modified.

```csharp
int[] numbers = new int[] { 1, 2, 3 };
ModifyValue(numbers);
Console.WriteLine(numbers[0]);
// Output: 2
```

In C#, primitive types such as `int`, `double`, `char`, and `bool` will be passed by value. Reference types such as `string`, `array`, and `class` will be passed by reference.

### `ref` and `out` - Explicit Reference Passing

### `ref`

Let's update the `ModifyValue` method to actually modify the value of the parameter. This can be done by using the `ref` or `out` keyword.

```csharp
// Method that modifies the value of a parameter
public static void ModifyValue(ref int value)
{
    value = 2;
}
```

When the method is called, the reference to the argument is copied to the parameter. When the parameter is modified, the value of the argument is also modified.

```csharp
int number = 1;
ModifyValue(ref number);
Console.WriteLine(number);
// Output: 2
```

### `out`

The `out` keyword is similar to the `ref` keyword. The difference is that the `out` keyword does not require the parameter to be initialized before it is passed to the method.

```csharp
// Method that modifies the value of a parameter
public static void ModifyValue(out int value)
{
    value = 2;
}
```

When the method is called, the reference to the argument is copied to the parameter. When the parameter is modified, the value of the argument is also modified.

```csharp
ModifyValue(out int number);
Console.WriteLine(number);
// Output: 2
```

