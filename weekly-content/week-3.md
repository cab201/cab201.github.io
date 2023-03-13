---
layout: default
title: Week 3 - Collections
nav_order: 4
permalink: /weekly-content/week-3
---

# Week 3 - Collections
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-3){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about collections in C#. A collection is a data structure that stores a group of elements.

## Arrays

An array is a collection of elements of the same type. There are two ways to declare an array:

```csharp
// Declare an array of double of size 5, without initializing it (all elements are set to 0)
double[] numbers = new double[5];
```

We can also declare and initialize an array in a single statement:

```csharp
// Declare and initialize an array of double
double[] numbers = new double[] { 1.0, 2.0, 3.0, 4.0, 5.0 };
```

### Accessing Array Elements

We can access the elements of an array using the index of the element. The index of an array starts from 0.

```csharp
// Declare and initialize an array of double
double[] numbers = new double[] { 1.0, 2.0, 3.0, 4.0, 5.0 };

// Access the first element of the array
Console.WriteLine(numbers[0]);
// Output: 1.0

// Change the value of the first element of the array
numbers[0] = 10.0;
```

The length of an array can be accessed using the `Length` property:

```csharp
// Declare and initialize an array of double
double[] numbers = new double[] { 1.0, 2.0, 3.0, 4.0, 5.0 };
Console.WriteLine(numbers.Length);
// Output: 5
```

It is common to use a `for` loop to iterate through the elements of an array. For example consider the following code to find an element in an array:

```csharp
// Declare and initialize an array of int
int[] numbers = new int[] { 1, 2, 3, 4, 5 };

// Find the index of the key element
int key = 3;
int index = -1; // -1 indicates that the key element is not found (default value)

for (int i = 0; i < numbers.Length; i++)
{
    if (numbers[i] == key)
    {
        index = i;
        break;
    }
}

// Print the index of the key element
Console.WriteLine(index);
// Output: 2
```

### Array Methods

Arrays have a number of useful methods that can be used to manipulate the elements of the array. Some of the most commonly used methods are:

| Method | Description |
| --- | --- |
| `Array.Reverse` | Reverses the order of the elements in the entire array. |
| `Array.Sort` | Sorts the elements in the entire array using the default comparer. |
| `Array.IndexOf` | Searches for the specified object and returns the index of the first occurrence within the entire array. |

Example:

```csharp
// Declare and initialize an array of int, in random order
int[] numbers = new int[] { 5, 3, 1, 4, 2 };

// Sort the array then print it using a for loop
Array.Sort(numbers);
for (int i = 0; i < numbers.Length; i++)
{
    Console.Write(numbers[i] + " ");
}
// Output: 1 2 3 4 5

// Reverse the array then print it using a foreach loop
Array.Reverse(numbers);
foreach (int number in numbers)
{
    Console.Write(number + " ");
}
// Output: 5 4 3 2 1

// Find the index of the key element then print it
int key = 2;
int index = Array.IndexOf(numbers, key);
Console.WriteLine(index);
// Output: 3
```

For more information about arrays, see the [Array Class](https://docs.microsoft.com/en-us/dotnet/api/system.array?view=net-6.0) documentation.

## Generic Collections

Generic collections are collections that can store elements of any type. To use generic collections, we need to import the `System.Collections.Generic` namespace by adding the following line at the top of the program:


```csharp
using System.Collections.Generic;

// Your program code goes here
namespace YourProjectNameHere
{
    class Program
    {
        static void Main(string[] args)
        {
            // ...
        }
    }
}
```

We will introduce two generic collections in this topic: `List<T>` and `Dictionary<TKey, TValue>`.

| Collection | Description |
| --- | --- |
| `List<T>` | A list is a collection of elements of the same type. It is similar to an array, but it can grow or shrink in size. |
| `Dictionary<TKey, TValue>` | A dictionary is a collection of key-value pairs. Each key is unique and is used to access its corresponding value. |

## Lists

A list is a collection of elements of the same type. It is similar to an array, but it can **grow or shrink in size**. There are two ways to declare a list:

```csharp
// Declare a list of int, without initializing it
List<int> numbers = new List<int>();
```

We can also declare and initialize a list in a single statement:

```csharp
// Declare and initialize a list of int
List<int> numbers = new List<int>() { 1, 2, 3, 4, 5 };
```

Lists can be used in a similar way to arrays (see the [Accessing Array Elements](#accessing-array-elements) section). However, lists have a number of useful methods that can be used to manipulate its elements. Some of the most commonly used methods are:

| Method | Description |
| --- | --- |
| `List.Add` | Adds an element to the end of the list. |
| `List.Remove` | Removes the first occurrence of the specified element from the list. |
| `List.Contains` | Determines whether the list contains the specified element. |
| `List.IndexOf` | Searches for the specified object and returns the index of the first occurrence within the entire list. |
| `List.Reverse` | Reverses the order of the elements in the entire list. |
| `List.Sort` | Sorts the elements in the entire list using the default comparer. |

Example:

```csharp
// Declare and initialize a list of int, in random order
List<int> numbers = new List<int>() { 5, 3, 1, 4, 2 };

// Sort the list then print it using a for loop
numbers.Sort();
for (int i = 0; i < numbers.Count; i++)
{
    Console.Write(numbers[i] + " ");
}
// Output: 1 2 3 4 5

// Reverse the list then print it using a foreach loop
numbers.Reverse();
foreach (int number in numbers)
{
    Console.Write(number + " ");
}
// Output: 5 4 3 2 1
```

For more information about lists, see the [List Class](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=net-6.0) documentation.

## Dictionaries

A dictionary is a collection of key-value pairs. Each key is unique and is used to access its corresponding value. There are two ways to declare a dictionary:

```csharp
// Declare a dictionary of int to string, without initializing it
Dictionary<string, int> postCodes = new Dictionary<string, int>();
```

We can also declare and initialize a dictionary in a single statement:

```csharp
// Declare and initialize a dictionary of int to string
Dictionary<string, int> postCodes = new Dictionary<string, int>()
{
    { "Brisbane", 4000 },
    { "Melbourne", 3000 },
    { "Sydney", 2000 },
    { "Perth", 6000 },
    { "Adelaide", 5000 }
};
```

To access a value in a dictionary, we use the key of the key-value pair:

```csharp
// Get the value of the key-value pair with key "Sydney"
int sydneyPostCode = postCodes["Sydney"];
Console.WriteLine(sydneyPostCode);
// Output: 2000
```

Dictionaries have a number of useful methods that can be used to manipulate its elements. Some of the most commonly used methods are:

| Method | Description |
| --- | --- |
| `Dictionary.Add` | Adds an element with the provided key and value to the dictionary. |
| `Dictionary.Remove` | Removes the element with the specified key from the dictionary. |
| `Dictionary.ContainsKey` | Determines whether the dictionary contains the specified key. |
| `Dictionary.ContainsValue` | Determines whether the dictionary contains the specified value. |

We can use the `Dictionary.Add` method to add a new key-value pair to the dictionary:

```csharp
// Add a new key-value pair to the dictionary
postCodes.Add("Canberra", 2600);

// Remove the key-value pair with key "Canberra"
postCodes.Remove("Canberra");

// Check if the dictionary contains the key "Brisbane"
bool containsKey = postCodes.ContainsKey("Brisbane");

// Check if the dictionary contains the value 2000
bool containsValue = postCodes.ContainsValue(2000);
```

Additionally, we can use the `Dictionary.Keys` and `Dictionary.Values` properties to get a collection of all the keys or values in the dictionary.

We can use the `Dictionary.Keys` property to get a collection of all the keys in the dictionary:

```csharp
foreach (string key in postCodes.Keys)
{
    Console.Write(key + " ");
}
// Output: Brisbane Melbourne Sydney Perth Adelaide

foreach (int value in postCodes.Values)
{
    Console.Write(value + " ");
}
// Output: 4000 3000 2000 6000 5000
```