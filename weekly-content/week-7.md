---
layout: default
title: Week 7 - Exceptions
nav_order: 7
permalink: /weekly-content/week-7
---

# Week 7 - Exceptions
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-7){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about exceptions in C#. An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.

## Exception Basics

### Throwing an Exception

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

To throw an exception, the `throw` keyword is used. The `throw` keyword is followed by an exception object. The exception object is created using the `new` keyword and the name of the exception class. The exception object is then passed to the `throw` keyword.

</details>

```csharp
throw new Exception("An exception has occurred");
```

### Catching an Exception

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

To catch an exception, the `try` and `catch` keywords are used. The `try` keyword is followed by a block of code that may throw an exception. The `catch` keyword is followed by a block of code that will be executed if an exception is thrown. The `catch` keyword is followed by the name of the exception class that will be caught. The `catch` block can be followed by a `finally` block, which will always be executed regardless of whether an exception is thrown.

</details>

```csharp
try
{
    // Code that may throw an exception
}
catch (Exception e)
{
    // Code that will be executed if an exception is thrown
}
finally
{
    // Code that will always be executed
}
```

### Common Exceptions

|Exception Class|Description|
|---|---|
|ArgumentException|Raiused when a non-null argument that is passed to a method is invalid|
|ArgumentNullException|Raised when a null argument is passed to a method|
|ArgumentOutOfRangeException|Raised when the value of a an argument is outside the range of valid values|
|DivideByZeroException|Raised when an integer value is divide by zero|
|FileNotFoundException|Raised when a physical file does not exist at the specified location|
|IndexOutOfRangeException|Raised when an array index is outside the lower or upper bound of an array or collection.|
|InvalidOperationException|RaisedWhen the specified key for accessing a member in a collection does not exist.|
|NotSupportedException|Raised when a method or operation is not supported|
|NullReferenceException|Raised when the program access members of null object|
|OverflowException|Raised when an arithmetic, casting or conversion operation results in an overflow|
|OutOfMemoryException|Raised when a program does not get enough memory to execute the code|
|StackOverflowException|Raised when the program does not get enough memory to execute the code|
|TimeoutException|Raised when the time interval allotted to an operation has expired|
|NotImplementedException|Raised when a method or property has not been implemented|


## A Detailed Example

<details closed markdown="block">
<summary>
    Click to show/hide explanation
</summary>

Consider the implimentation of a bank account class. The bank account class has a `Balance` property that contains the current balance of the account. The `Withdraw` method is used to withdraw money from the account, the `Deposit` method is used to deposit money into the account, and the `Transfer` method is used to transfer money from one account to another.

The `BadBankAccount` class below does not handle the exceptional cases of withdrawing more money than is in the account or transferring more money than is in the account, leading to the balance of the account becoming negative.

</details>

<mark><b>
THIS IS A BAD EXAMPLE. DO NOT USE THIS CODE IN YOUR PROGRAMS.
</b></mark>

```csharp
public class Program
{
    public static void Main()
    {
        // Bug: Account balance can become negative
        BadBankAccount account1 = new BadBankAccount(-100);
        BadBankAccount account2 = new BadBankAccount(100);

        // Bug: Withdraw more money than is in the account
        account1.Withdraw(200);
        Console.WriteLine(account1.Balance); // -300

        // Bug: Transfer more money than is in the account
        account1.Transfer(account2, 200);
        Console.WriteLine(account1.Balance); // -500

        // Bug: Withdraw negative money (making money out of thin air)
        account1.Withdraw(-100);
        Console.WriteLine(account1.Balance); // -200

        // Bug: Negative transfer (stealing money, basically...)
        account2.Transfer(account1, -1000);
        Console.WriteLine(account1.Balance); // 500
    }
}

public class BadBankAccount {
    public double Balance { get; private set; }
    public BadBankAccount(double balance) {
        Balance = balance;
    }

    public void Withdraw(double amount) {
        Balance -= amount;
    }

    public void Deposit(double amount) {
        Balance += amount;
    }

    public void Transfer(BadBankAccount other, double amount) {
        Withdraw(amount);
        other.Deposit(amount);
    }
}
```

The `GoodBankAccount` class below handles the exceptional cases of withdrawing more money than is in the account or transferring more money than is in the account, by throwing an exception.

```csharp
public class Program
{
    public static void Main()
    {
        GoodBankAccount account1, account2;
        
        // Cannot create account with negative balance
        try
        {
            account1 = new GoodBankAccount(-100); // Exception: Cannot create account with negative balance
            account2 = new GoodBankAccount(100); // This line will not be executed
        }
        catch (ArgumentException e)
        {
            Console.WriteLine(e.Message); // Cannot create account with negative balance
            account1 = new GoodBankAccount(100);
            account2 = new GoodBankAccount(100);
            return;
        }

        // Cannot overdraw account
        try
        {
            for (int i = 0; i < 3; i++){
                account1.Withdraw(50); // Throws exception on third iteration
                Console.WriteLine(account1.Balance); // 50, 0
            }
        }
        catch (ArgumentException e)
        {
            Console.WriteLine(e.Message); // Insufficient funds
        }

        // Cannot transfer more money than is in the account
        try
        {
            account1.Transfer(account2, 200); // Exception: Insufficient funds
            Console.WriteLine(account1.Balance); // This line will not be executed
        }
        catch (ArgumentException e)
        {
            Console.WriteLine(e.Message); // Insufficient funds
        }

        // Cannot withdraw negative amount
        try
        {
            account1.Withdraw(-100); // Exception: Cannot withdraw negative amount
            Console.WriteLine(account1.Balance); // This line will not be executed
        }
        catch (ArgumentException e)
        {
            Console.WriteLine(e.Message); // Cannot withdraw negative amount
        }

        // Cannot transfer negative amount
        try
        {
            account2.Transfer(account1, -100); // Exception: Cannot transfer negative amount
            Console.WriteLine(account1.Balance); // This line will not be executed
        }
        catch (ArgumentException e)
        {
            Console.WriteLine(e.Message); // Cannot transfer negative amount
        }

        // Display final balances
        Console.WriteLine(account1.Balance); // 0
        Console.WriteLine(account2.Balance); // 100
    }
}

public class GoodBankAccount {
    public double Balance { get; private set; }
    public GoodBankAccount(double balance) {
        if (balance < 0)
        {
            throw new ArgumentException("Cannot create account with negative balance");
        }
        Balance = balance;
    }

    public void Withdraw(double amount) {
        if (amount < 0)
        {
            throw new ArgumentException("Cannot withdraw negative amount");
        }
        if (amount > Balance)
        {
            throw new ArgumentException("Insufficient funds");
        }
        Balance -= amount;
    }

    public void Deposit(double amount) {
        if (amount < 0)
        {
            throw new ArgumentException("Cannot deposit negative amount");
        }
        Balance += amount;
    }

    public void Transfer(GoodBankAccount other, double amount) {
        if (amount < 0)
        {
            throw new ArgumentException("Cannot transfer negative amount");
        }
        if (amount > Balance)
        {
            throw new ArgumentException("Insufficient funds");
        }
        Withdraw(amount);
        other.Deposit(amount);
    }
}
```