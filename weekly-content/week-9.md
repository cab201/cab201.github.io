---
layout: default
title: Week 9 - Polymorphism
nav_order: 9
permalink: /weekly-content/week-9
---

# Week 9 - Polymorphism
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-10){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about polymorphism in C#. Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in C# occurs when a parent class reference is used to refer to a child class object.

## Polymorphism

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in C# occurs when a parent class reference is used to refer to a child class object.

</details>

```csharp
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Grrr");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow");
    }
}

public class Program
{
    public static void Main()
    {
        Animal unknownAnimal = new Animal();
        Animal dog = new Dog();
        Animal cat = new Cat();

        unknownAnimal.MakeSound(); // Grrr
        dog.MakeSound(); // Woof
        cat.MakeSound(); // Meow
    }
}
```

## Abstract Classes

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Abstract classes are classes that cannot be instantiated. They can only be inherited from. Abstract classes are declared using the `abstract` keyword. Abstract classes can contain abstract methods, which are methods that do not have a body. Abstract methods are declared using the `abstract` keyword and are followed by a semicolon, rather than a body. Abstract methods must be implemented in the child class.

</details>

```csharp
public abstract class Animal
{
    public abstract void MakeSound();
    public virtual void Eat()
    {
        Console.WriteLine("Eating some food");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof");
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow");
    }
    public override void Eat()
    {
        // Cats are picky eaters, so they only eat cat food
        Console.WriteLine("Eating cat food");
    }
}

public class Program
{
    public static void Main()
    {
        Animal dog = new Dog();
        Animal cat = new Cat();

        dog.MakeSound(); // Woof
        cat.MakeSound(); // Meow

        dog.Eat(); // Eating some food
        cat.Eat(); // Eating cat food

        Animal unknownAnimal = new Animal(); // Error: Cannot create an instance of the abstract class or interface 'Animal'
    }
}
```

## Interfaces

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Interfaces are similar to abstract classes, but they cannot contain any implementation. All methods in an interface are abstract by default. Interfaces are declared using the `interface` keyword. Interfaces can be implemented by classes using the `:` operator.

</details>

```csharp
public interface IAnimal
{
    void MakeSound();
    void Eat();
}

public interface IFlyable
{
    void Fly();
}

public interface IWalkable
{
    void Walk();
}

public interface ISwimmable
{
    void Swim();
}

public class Dog : IAnimal, IWalkable
{
    public void MakeSound()
    {
        Console.WriteLine("Woof");
    }
    public void Eat()
    {
        Console.WriteLine("Eating some food");
    }
    public void Walk()
    {
        Console.WriteLine("Walking");
    }
}

public class Dove : IAnimal, IFlyable
{
    public void MakeSound()
    {
        Console.WriteLine("Coo");
    }
    public void Eat()
    {
        Console.WriteLine("Eating breadcrumbs");
    }
    public void Fly()
    {
        Console.WriteLine("Flying");
    }
}

public class Fish : IAnimal, ISwimmable
{
    public void MakeSound()
    {
        Console.WriteLine("Blub");
    }
    public void Eat()
    {
        Console.WriteLine("Eating smaller fish");
    }
    public void Swim()
    {
        Console.WriteLine("Swimming");
    }
}

public class Duck : IAnimal, IFlyable, IWalkable, ISwimmable
{
    public void MakeSound()
    {
        Console.WriteLine("Quack");
    }
    public void Eat()
    {
        Console.WriteLine("Eating corn");
    }
    public void Fly()
    {
        Console.WriteLine("Flying");
    }
    public void Walk()
    {
        Console.WriteLine("Walking");
    }
    public void Swim()
    {
        Console.WriteLine("Swimming");
    }
}

public class Program
{
    public static void Main()
    {
        Dog dog = new Dog();
        Dove dove = new Dove();
        Fish fish = new Fish();
        Duck duck = new Duck();

        // Since all of the classes implement the IAnimal interface, we can use an array of IAnimal to store all of the classes
        IAnimal[] animals = new IAnimal[] { dog, dove, fish, duck };
        foreach (IAnimal animal in animals)
        {
            animal.MakeSound(); // Woof, Coo, Blub, Quack
            animal.Eat(); // Eating some food, Eating breadcrumbs, Eating smaller fish, Eating corn

            // Since animal is an IAnimal, we can't access the methods that are specific to the other interfaces
            // animal.Walk(); // Error: 'IAnimal' does not contain a definition for 'Walk'...

            // However, we can use the `is` keyword to check if the class implements the interface
            if (animal is IWalkable)
            {
                IWalkable walkableAnimal = (IWalkable)animal;
                walkableAnimal.Walk(); // Walking, Walking
            }
            if (animal is IFlyable)
            {
                IFlyable flyableAnimal = (IFlyable)animal;
                flyableAnimal.Fly(); // Flying
            }
            if (animal is ISwimmable)
            {
                ISwimmable swimmableAnimal = (ISwimmable)animal;
                swimmableAnimal.Swim(); // Swimming
            }
        }

        // Outside of the foreach loop, we can access the methods that are specific to the other interfaces
        dog.Walk(); // Walking
        dove.Fly(); // Flying
        fish.Swim(); // Swimming

        duck.Walk(); // Walking
        duck.Fly(); // Flying
        duck.Swim(); // Swimming

        // Although we can instantiate the IAnimal through the Duck class, this only gives us access to the methods in the IAnimal interface
        IAnimal duckByInterface = new Duck();
        duckByInterface.MakeSound(); // Quack
        duckByInterface.Eat(); // Eating corn
        // duckByInterface.Walk(); // Error: 'IAnimal' does not contain a definition for 'Walk'...
        // duckByInterface.Fly(); // Error: 'IAnimal' does not contain a definition for 'Fly'...
        // duckByInterface.Swim(); // Error: 'IAnimal' does not contain a definition for 'Swim'...

        // We can use the `as` keyword to cast the IAnimal to the Duck class
        Duck duckByClass = duckByInterface as Duck;
        duckByClass.MakeSound(); // Quack
        duckByClass.Eat(); // Eating corn
        duckByClass.Walk(); // Walking
        duckByClass.Fly(); // Flying
        duckByClass.Swim(); // Swimming
    }
}
```