---
layout: default
title: Week 5 - Streams
nav_order: 6
permalink: /weekly-content/week-5
---

# Week 5 - Streams
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

[Do the Practical](../practicals/week-5){: .btn .btn-blue .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

In this topic, we will learn about streams in C#. A stream is a sequence of bytes that can be read from or written to. Streams are used to read and write data from and to files, network connections, and other sources in a sequential manner.

## Directory and File I/O

### Documenting the File System

The `System.IO` namespace contains classes that allow you to work with files and directories. 

Class | Description
--- | ---
`Directory` | Contains methods for creating, moving, and enumerating through directories and subdirectories.
`File` | Contains static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of `FileStream` objects.
`DirectoryInfo` | Contains non-static methods for creating, moving, and enumerating through directories and subdirectories.
`FileInfo` | Contains non-static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of `FileStream` objects.

### Checking for the Existence of a File or Directory

The `File` and `Directory` classes contain methods that allow you to check whether a file or directory exists.

Method | Description
--- | ---
`Directory.Exists(path)` | Returns a boolean value indicating whether the specified directory exists.
`File.Exists(path)` | Returns a boolean value indicating whether the specified file exists.

For example, the following code checks whether the `C:\Users\Public\Documents` directory exists, then checks whether the `C:\Users\Public\Documents\MyFile.txt` file exists.

```csharp
if (Directory.Exists("C:\Users\Public\Documents"))
{
    // Directory exists
    if (File.Exists("C:\Users\Public\Documents\MyFile.txt"))
    {
        // File exists
    }
    else
    {
        // File does not exist
    }
}
else
{
    // Directory does not exist
}
```

### Information About a File or Directory

The `Directory` and `File` classes contain methods that allow you to get information about a file or directory.

Method | Description
--- | ---
`Directory.GetCreationTime()` | Returns the creation date and time of the specified directory.
`Directory.GetLastAccessTime()` | Returns the date and time the specified directory was last accessed.
`Directory.GetLastWriteTime()` | Returns the date and time the specified directory was last written to.
`File.GetCreationTime()` | Returns the creation date and time of the specified file.
`File.GetLastAccessTime()` | Returns the date and time the specified file was last accessed.
`File.GetLastWriteTime()` | Returns the date and time the specified file was last written to.

For example, the following code gets the creation date and time of the `C:\Users\Public\Documents` directory, then gets the creation date and time of the `C:\Users\Public\Documents\MyFile.txt` file.

```csharp
Console.WriteLine(Directory.GetCreationTime("C:\Users\Public\Documents"));
Console.WriteLine(File.GetCreationTime("C:\Users\Public\Documents\MyFile.txt"));
```

### Listing Files and Directories

The `Directory` class contain methods that allow you to list files and directories.

Method | Description
--- | ---
`Directory.GetFiles()` | Returns an array of strings containing the names of files (including their paths) in the specified directory.
`Directory.GetDirectories()` | Returns an array of strings containing the names of subdirectories (including their paths) in the specified directory.

For example, the following code lists all the files in the `C:\Users\Public\Documents` directory, then lists all the subdirectories in the `C:\Users\Public\Documents` directory.

```csharp
foreach (string file in Directory.GetFiles("C:\Users\Public\Documents"))
{
    Console.WriteLine(file);
}

foreach (string directory in Directory.GetDirectories("C:\Users\Public\Documents"))
{
    Console.WriteLine(directory);
}
```

## File Reading

To read from a file, you can use a `StreamReader` object.

The following code creates a `StreamReader` object to read from the `C:\Users\Public\Documents\MyFile.txt`, then displays each line of the file.

```csharp
using (StreamReader reader = new StreamReader("C:\Users\Public\Documents\MyFile.txt"))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}
```

Alternatively, use `!readline.EndOfStream` to read through the file.

```csharp
string path = "C:\Users\Public\Documents\MyFile.txt";
using (StreamReader reader = new StreamReader(path))
{
    string line = null;
    // Read through the whole file
    do
    {
        line = reader.ReadLine();
        Console.WriteLine(line);
    } while (!reader.EndOfStream);
}
```

Note that the `using` statement is used to ensure that the `StreamReader` object is disposed of correctly. If you do not use the `using` statement, you must call the `StreamReader.Close()` method to dispose of the object.

## File Writing

To write to a file, you can use a `StreamWriter` object.

The following code creates a `StreamWriter` object to write to the `C:\Users\Public\Documents\MyFile.txt`, then writes the text "Hello World!" to the file.

```csharp
using (StreamWriter writer = new StreamWriter("C:\Users\Public\Documents\MyFile.txt"))
{
    writer.WriteLine("Hello World!");
}
```

## Command Line Arguments

The `Main` method of a C# program can accept command line arguments. These arguments are passed to the program as an array of strings.

For example, the following code displays the command line arguments passed to the program.

```csharp
static void Main(string[] args)
{
    foreach (string arg in args)
    {
        Console.WriteLine(arg);
    }
}
```

In Visual Studio, you can pass command line arguments to a program by right-clicking the project in the Solution Explorer, then selecting **Properties**. In the **Debug** tab, enter the command line arguments in the **Command line arguments** box.