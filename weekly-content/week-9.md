---
layout: default
title: Week 9 - Inheritance
nav_order: 9
permalink: /weekly-content/week-9
---

# Week 9 - Inheritance
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-9){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about inheritance in C#. Inheritance is a mechanism that allows a class to inherit the members of another class for reuse. Inheritance is a powerful feature of object-oriented programming languages.

## Inheritance

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Inheritance is a mechanism that allows a class to inherit the members of another class. The class that inherits the members of another class is called the derived class. The class that is inherited from is called the base class. The derived class inherits the members of the base class, but can also add its own members, or override the members of the base class.

In C#, inheritance is achieved using the `:` symbol after the name of the class. The class that is inherited from is placed after the `:` symbol.

</details>

```csharp
class BaseClass
{
    public string BaseProperty { get; }

    public BaseClass(string baseProperty)
    {
        BaseProperty = baseProperty;
    }

    public void BaseMethod()
    {
        Console.WriteLine("Base method");
    }
}

class DerivedClass : BaseClass // Use the : symbol to inherit from a base class
{
    public string DerivedProperty 
    {
        get 
        {
            return String.Format("{0} as derived property", BaseProperty);
        }
    }

    public void DerivedMethod()
    {
        Console.WriteLine("Derived method");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // The base class has a base property and a base method, defined
        // in the BaseClass class
        BaseClass baseClass = new BaseClass("Base property");
        baseClass.BaseMethod(); // Base method
        Console.WriteLine(baseClass.BaseProperty); // Base property

        // Although we did not define a BaseMethod() and BaseProperty in the DerivedClass,
        // inheritance allows us to use the BaseMethod() and BaseProperty from the BaseClass 
        DerivedClass derivedClass = new DerivedClass("Base property");
        derivedClass.BaseMethod(); // Base method
        Console.WriteLine(derivedClass.BaseProperty); // Base property

        // And also extend with the DerivedMethod() and DerivedProperty
        derivedClass.DerivedMethod(); // Derived method
        Console.WriteLine(derivedClass.DerivedProperty); // Base property as derived property
    }
}
```

## Overriding - `override`, `virtual` and `base`

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Inheritance allows a derived class to inherit the members of a base class. However, the derived class can also override the members of the base class. This is useful when the derived class needs to provide a different implementation of a member of the base class.

In C#, to allow a derived class to override a member of the base class, the member must be marked with the `virtual` keyword. The `virtual` keyword is used to mark a member as being able to be overridden in a derived class. The `virtual` keyword can be used on methods and properties.

To override a member of the base class, the derived class must use the `override` keyword. The `override` keyword is used to mark a member as being overridden in a derived class. The `override` keyword can be used on methods and properties.

</details>

Consider the previous example, but with the `BaseProperty` and `BaseMethod` marked as `virtual` in the `BaseClass` class, then overridden in the `DerivedClass` class.

```csharp

class BaseClass
{
    // Use the virtual keyword to allow a derived class to override a member
    public virtual string BaseProperty { get; }

    public BaseClass(string baseProperty)
    {
        BaseProperty = baseProperty;
    }

    public virtual void BaseMethod()
    {
        Console.WriteLine("Base method");
    }
}

class DerivedClass : BaseClass
{
    public string DerivedProperty 
    {
        get 
        {
            return String.Format("{0} as derived property", BaseProperty);
        }
    }

    // Use the override keyword to override a base class member
    public override string BaseProperty
    {
        get
        {
            // Use the base keyword to access the base class member
            return base.BaseProperty + ", overridden";
        }
    }

    public override void BaseMethod() 
    {
        Console.WriteLine("Base method, overridden");
    }

    public void DerivedMethod()
    {
        Console.WriteLine("Derived method");
    }
}

class Program {
    static void Main(string[] args)
    {
        // The base class has a base property and a base method, defined
        // in the BaseClass class
        BaseClass baseClass = new BaseClass("Base property");
        baseClass.BaseMethod(); // Base method
        Console.WriteLine(baseClass.BaseProperty); // Base property

        // Although we did not define a BaseMethod() and BaseProperty in the DerivedClass,
        // inheritance allows us to use the BaseMethod() and BaseProperty from the BaseClass 
        DerivedClass derivedClass = new DerivedClass("Base property");
        derivedClass.BaseMethod(); // Base method, overridden
        Console.WriteLine(derivedClass.BaseProperty); // Base property, overridden

        // And also extend with the DerivedMethod() and DerivedProperty
        derivedClass.DerivedMethod(); // Derived method
        Console.WriteLine(derivedClass.DerivedProperty); // Base property as derived property
    }
}
```

## Overriding the Constructor

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

The constructor of a class cannot be marked as `virtual` or `override`. However, the constructor of a derived class can extend the constructor of the base class by using the `base` keyword.

This will call the constructor of the base class, and then the derived class constructor will execute.

</details>

Consider the following example, where `Student` is derived from `Person`. The `Student` class overrides the `Person` class constructor, and calls the `Person` class constructor using the `base` keyword.

```csharp
class Person
{
    public int Id { get; }
    public string Name { get; }
    public string Email { get; }

    public Person(int id, string name, string email)
    {
        Id = id;
        Name = name;
        Email = email;
    }
}

class Unit {
    public string Code { get; }
    public string Name { get; }

    public Unit(string code, string name)
    {
        Code = code;
        Name = name;
    }
}

class Student : Person
{
    private List<Unit> enrolments;

    // Use the base keyword to call the base class constructor,
    // initializing the Id, Name, and assign a QUT email address
    public Student(int id, string name) : base(id, name, $"{id}@qut.edu.au")
    {
        // After the base class constructor has executed, this constructor
        // will execute, and we can initialize the enrolments list
        enrolments = new List<Unit>();
    }

    public void Enrol(Unit unit)
    {
        enrolments.Add(unit);
    }

    public void PrintEnrolments()
    {
        Console.WriteLine($"Enrolments for {Name} ({Id})");
        foreach (Unit unit in enrolments)
        {
            Console.WriteLine($"{unit.Code} - {unit.Name}");
        }
    }
}

class Program {
    static void Main(string[] args)
    {
        Unit cab201 = new Unit("CAB201", "Programming Principles");
        Unit cab203 = new Unit("CAB203", "Discrete Structures");
        Unit cab230 = new Unit("CAB230", "Web Computing");
        Unit cab202 = new Unit("CAB202", "Microprocessors");

        Student student = new Student(12345678, "John Smith");
        student.Enrol(cab201);
        student.Enrol(cab202);
        student.Enrol(cab203);
        student.Enrol(cab230);
        student.PrintEnrolments();
        // Enrolments for John Smith (12345678)
        // CAB201 - Programming Principles
        // CAB202 - Microprocessors
        // CAB203 - Discrete Structures
        // CAB230 - Web Computing

        // The student can also access the Id, Name, and Email properties
        // from the Person class
        Console.WriteLine($"{student.Name} ({student.Id}) - {student.Email}");
        // John Smith (12345678) - 12345678@qut.edu.au
    }
}
```

## `protected` Access Modifier

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

The `protected` access modifier is similar to the `private` access modifier, except that it allows derived classes to access the member.

</details>

Consider the following example, where the `BaseClass` has a `protected` member, and the `DerivedClass` can access the `protected` member.

```csharp
class BaseClass
{
    protected string ProtectedMember { get; }

    public BaseClass(string protectedMember)
    {
        ProtectedMember = protectedMember;
    }
}

class DerivedClass : BaseClass
{
    public DerivedClass(string protectedMember) : base(protectedMember)
    {
    }

    public void PrintProtectedMember()
    {
        Console.WriteLine(ProtectedMember);
    }
}

class Program {
    static void Main(string[] args)
    {
        DerivedClass derivedClass = new DerivedClass("Protected member");
        derivedClass.PrintProtectedMember(); // Protected member

        // The following line will not compile, because the ProtectedMember
        // is protected, and cannot be accessed outside of the BaseClass
        // or DerivedClass
        Console.WriteLine(derivedClass.ProtectedMember);
    }
}
```

## Overriding the Object Methods - `ToString()`, `Equals()`, and `GetHashCode()`

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

The `ToString()`, `Equals()`, and `GetHashCode()` methods are defined in the `System.Object` class, and are used to convert an object to a string, compare two objects, and get the hash code of an object.

The `ToString()` method is used to convert an object to a string. The `Equals()` method is used to compare two objects. The `GetHashCode()` method is used to get the hash code of an object.

</details>

Consider the following example, where the `Person` class overrides the `ToString()` method, and the `Student` class overrides the `Equals()` and `GetHashCode()` methods.

```csharp

class Person
{
    public int Id { get; }
    public string Name { get; }
    public string Email { get; }

    public Person(int id, string name, string email)
    {
        Id = id;
        Name = name;
        Email = email;
    }

    public override bool Equals(object obj)
    {
        if (obj is Person person)
        {
            return Id == person.Id;
        }
        return false;
    }

    public override int GetHashCode()
    {
        return Id;
    }

    public override string ToString()
    {
        return $"{Name} ({Id}) - {Email}";
    }
}

class Student : Person
{
    private List<Unit> enrolments;

    public Student(int id, string name) : base(id, name, $"{id}.qut.edu.au")
    {
        enrolments = new List<Unit>();
    }

    public void Enrol(Unit unit)
    {
        enrolments.Add(unit);
    }

    // Student objects are equal if they have the same Id
    public override bool Equals(object obj)
    {
        if (obj is Student student)
        {
            return Id == student.Id;
        }
        return false;
    }

    // Student objects have the same hash code if they have the same Id
    public override int GetHashCode()
    {
        return Id;
    }

    public void PrintEnrolments()
    {
        Console.WriteLine($"Enrolments for {Name} ({Id})");
        foreach (Unit unit in enrolments)
        {
            Console.WriteLine($"{unit.Code} - {unit.Name}");
        }
    }

    public override string ToString()
    {
        string enrolmentsString = "";
        for (int i = 0; i < enrolments.Count; i++)
        {
            Unit unit = enrolments[i];
            enrolmentsString += $"{unit.Code} - {unit.Name}";
            if (i < enrolments.Count - 1)
            {
                enrolmentsString += ", ";
            }
        }
        return $"{Name} ({Id}) - {Email} - Enrolments: {enrolmentsString}";
    }
}

class Program {
    static void Main(string[] args)
    {
        Unit cab201 = new Unit("CAB201", "Programming Principles");
        Unit cab203 = new Unit("CAB203", "Discrete Structures");
        Unit cab230 = new Unit("CAB230", "Web Computing");
        Unit cab202 = new Unit("CAB202", "Microprocessors");

        Student student = new Student(12345678, "John Smith");
        student.Enrol(cab201);
        student.Enrol(cab202);
        student.Enrol(cab203);
        student.Enrol(cab230);

        // The Student class overrides the ToString() method, so the
        // following line will print the string returned by the
        // ToString() method
        Console.WriteLine(student);
        // John Smith (12345678) - 12345678@qut.edu.au - Enrolments: CAB201 - Programming Principles, CAB202 - Microprocessors, CAB203 - Discrete Structures, CAB230 - Web Computing

        Student student2 = new Student(12345678, "John Smith");

        // The Student class overrides the Equals() and GetHashCode() methods,
        // so the following lines will return true
        Console.WriteLine(student.Equals(student2)); // True
        Console.WriteLine(student.GetHashCode() == student2.GetHashCode()); // True

        // Note that comparing two objects using the == operator will
        // return false, because the == operator compares the references
        // of the objects, not the values of the objects
        Console.WriteLine(student == student2); // False
    }
}
```