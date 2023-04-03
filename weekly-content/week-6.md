---
layout: default
title: Week 6 - Classes
nav_order: 7
permalink: /weekly-content/week-6
---

# Week 6 - Classes
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-6){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about classes in C#. A class is a data type that can contain data fields and methods. Classes are used to create objects, which are instances of the class.

## Class Basics

A class is created using the `class` keyword and can contain the following members:

- `Fields`: Variables that contain data.
- `Methods`: A block of code that performs a specific task.
- `Properties`: A member that provides a flexible mechanism to read, write, or compute the value of a private field.

A class is defined using the following syntax:

```csharp
access_modifier class ClassName
{
    // Field
    access_modifier type fieldName;

    // Property
    access_modifier type propertyName
    {
        // Note that the access modifiers for the get and set accessors can be different
        set_access_modifier get
        {
            // Property get body
        }
        get_access_modifier set
        {
            // Property set body
        }
    }

    // Method
    access_modifier return_type methodName(parameter_list)
    {
        // Method body
    }
}
```

In C#, a class can be placed in a different file from the `Program`. In this case, the class must be declared as `public`.

### Visibility Modifiers

The visibility of a class member determines whether it can be accessed from outside the class. In CAB201, we will focus on the following visibility modifiers:

| Modifier | Description |
| --- | --- |
| `public` | The member can be accessed from outside the class. |
| `private` | The member can only be accessed from within the class. |
| `protected` | The member can only be accessed from within the class or from within a class that inherits from it. |

The following example creates a class named `Person` that contains a field named `name` and a method named `SayHello`.

**Note that this is a bad practice, as we will see later**.

```csharp
class Person
{
    // Field
    public string name;

    // Method
    public void SayHello()
    {
        Console.WriteLine("Hello! My name is " + name);
    }
}
```

### Working with Objects

An object is an instance of a class. An object is created using the `new` keyword. The following example creates an object named `person1` of type `Person`:

```csharp
Person person1 = new Person();
```

You can access the members of an object using the dot operator. The following example accesses the `name` field and the `SayHello` method of the `person1` object:

```csharp
person1.name = "John";
person1.SayHello();
// Output: Hello! My name is John
```

### Constructors

A constructor is a special method that is called when an object of a class is created. Constructors are used to initialize fields of the class. Constructors have the same name as the class. The following example creates a constructor for the `Person` class:

```csharp
class Person
{
    // Field
    public string name;

    // Constructor
    public Person(string name)
    {
        // The this keyword refers to the current instance of the class
        // use this to distinguish between the fields and the parameters with the same name
        this.name = name;
    }

    // Method
    public void SayHello()
    {
        Console.WriteLine("Hello! My name is " + name);
    }
}
```

The following example creates an object named `person1` of type `Person` and passes the string `"John"` to the constructor:

```csharp
Person person1 = new Person("John");
// Output: Hello! My name is John
```

#### Overloading Constructors

Like any method, you can overload a constructor. The following example creates two constructors for the `Person` class:

```csharp
class Person
{
    // Field
    public string name;

    // Constructor
    public Person()
    {
        name = "John";
    }

    public Person(string name)
    {
        this.name = name;
    }

    // Method
    public void SayHello()
    {
        Console.WriteLine("Hello! My name is " + name);
    }
}
```

The following example creates two objects named `person1` and `person2` of type `Person`:

```csharp
Person person1 = new Person();
Person person2 = new Person("Mary");
person1.SayHello();
// Output: Hello! My name is John
person2.SayHello();
// Output: Hello! My name is Mary
```

### Properties

A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field. This enables data to be accessed easily and still helps to ensure the validity of the data. 

The following example creates a property named `Name` for the `Person` class that operates on the `name` field.
- The `get` accessor returns the value of the `name` field.
- The `set` accessor sets the value of the `name` field while ensuring that the value is not an empty string, and that the first letter is capitalized. If the value is empty, set the `name` field to `"Invalid"`. If the first letter is not capitalized, capitalize it.

Note that the constructor is modified to use the `Name` property instead of the `name` field.

```csharp
class Person
{
    // Field
    private string name;

    // Property
    public string Name
    {
        get
        {
            return name;
        }
        set
        {
            // Ensure that the value is not an empty string
            if (value.Length == 0)
            {
                name = "Invalid";
            }
            // If the first letter is not capitalized, capitalize it
            else if (char.IsLower(value[0]))
            {
                string capitalisedName = value[0].ToString().ToUpper();
                for (int i = 1; i < value.Length; i++)
                {
                    capitalisedName += value[i];
                }
                name = capitalisedName;
            }
            // Otherwise, set the name field to the value
            else
            {
                name = value;
            }
        }
    }

    // Constructor
    public Person(string name)
    {
        Name = name;
    }

    // Method
    public void SayHello()
    {
        Console.WriteLine("Hello! My name is " + name);
    }
}
```

The following example creates a `Person`, originally invalid, and then sets the `Name` property to a valid value:

```csharp
Person person1 = new Person("");
person1.SayHello();
// Output: Hello! My name is Invalid

person1.Name = "John";
person1.SayHello();
// Output: Hello! My name is John

person1.Name = "mary";
person1.SayHello();
// Output: Hello! My name is Mary
```

### Has-A Relationship

A class can contain another class as a field. This is called a **has-a** relationship. The following example creates a `House` class that contains a `Person` field named `owner`, and a `List<Person>` field named `occupants`.

We say that `House` **depends on** `Person`, and that `Person` is a **part of** `House`.

```csharp
class House
{
    // Fields
    public Person owner;
    public List<Person> occupants;

    // Constructor
    public House(Person owner)
    {
        this.owner = owner;
        occupants = new List<Person>();
    }

    // Overloaded constructor to create a House with occupants
    public House(Person owner, params Person[] occupants)
    {
        this.owner = owner;
        this.occupants = new List<Person>(occupants);
    }
    
    // Method to add an occupant
    public void AddOccupant(Person occupant)
    {
        occupants.Add(occupant);
    }

    // Method to display the owner and occupants
    public void Display()
    {
        Console.WriteLine("Owner: " + owner.Name);
        Console.WriteLine("Occupants:");
        foreach (Person occupant in occupants)
        {
            Console.WriteLine(occupant.Name);
        }
    }
}
```

The following example creates a `House` and adds occupants to it:

```csharp
Person owner = new Person("John");
Person person1 = new Person("Mary");
Person person2 = new Person("Peter");
Person person3 = new Person("Jane");

House house1 = new House(owner, person1, person2, person3);
house1.AddOccupant(new Person("Tom"));
house1.Display();
// Output:
// Owner: John
// Occupants:
// Mary
// Peter
// Jane
// Tom
```