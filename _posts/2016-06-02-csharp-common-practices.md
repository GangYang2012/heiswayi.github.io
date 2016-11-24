---
layout: post
title: C# Common Practices
description: Good coding practices make code looks professional and self-documented.
keywords: csharp common practices, self-documented code, code optimization, good coding practices
---

This article may not be as unique as you are expected to be. Because out there, if you're friendly enough with Mr. Google, you will find something more similar to this article. Even so, I still want to note this as a reminder to myself whenever I do programming in C#, and also might help or as a common guideline to the new C# developers.

### Use of Proper Naming Conventions

Use of proper naming conventions ensure you an easy way to maintain your code, especially when the software is big or has thousand lines of code.

---

> Always use Camel case or Pascal when declaring variables/properties.

Camel case is a word with the first letter lowercase, while others are capitalized. Pascal case is a word the first letter capitalized and followed by others.

Example:

```csharp
// Declaring variables using Camel case
private double numberOfSamples;
private int primeNumber;
private object myObject

// Declaring public properties using Pascal case
public double Distance { get; set; }
public int NumberOfChannels { get; }
public object MyObject { get; private set; }

// Private methods using Camel case
private bool isValid(double value) { ... }
private void getUrlFromServer() { ... }

// Public methods using Pascal case
public double GetNumberOfSamples() { ... }
public bool IsUrlWorking(string url) { ... }
```

---

> Use all uppercase when declaring constant variables.

Example:

```csharp
public const int INVALID_VALUE = -1;
public const string ERROR_MSG = "Application crashed. Please check the log file."
```

---

> Never use a name that begins with a numeric character.

Instead of `1Person`, you can define as `OnePerson`.

---

> Always use meaningful names for class, property, method, variable, etc. Make it easily understandable. Good code is self-documented.

Example: Instead of `Meas` class name, best to put in a complete term as `Measurement`.

---

> If you can, just avoid adding prefixes or suffixes for your identifiers. However, this is subjective/optional depending on your organization coding practices.

As far as I know, it's not that much useful to add prefix like `m_` or `_` to your variable declaration. But if you still want to use it, that's okay for me if you think by adding those prefixes will help your code looks much more readable in recognizing the variable of `private` members.

---

> Always use `I` as a prefix for Interface. This is a common practice for declaring interfaces.

Example:

```csharp
public interface IMyInterface
{
  void MethodToImplement(); // Abstract method signature
  double MyProperties { get; }
}

public class MyInterfaceImplementer : IMyInterface
{
  // Constructor
  public MyInterfaceImplementer()
  {
    MyInterfaceImplementer obj = new MyInterfaceImplementer();
    obj.MethodToImplement();
  }

  public void MethodToImplement()
  {
    // Abstract method implementation here
  }
}
```

---

> Always add `Exception` as suffix for your custom exception class. This will give better visibility to your exception class.

Example:

```csharp
public class LoginException : System.exception
{
  // TODO stuffs here...
}
```

---

> Never prefix or suffix the class name to its property names.

Example:

```csharp
public class Person
{
  public string PersonFirstname { get; set; } // [❌] DON'T DO THIS
  public string Firstname { get; set; } // [✓] DO THIS INSTEAD
}

static void Main()
{
  // Because you can easily identify it from that class directly.
  Person person = new Person();
  Console.WriteLine(person.Firstname); // <--
}
```

---

> Recommended to use prefix like `Is`, `Has` or `Can` for Boolean properties, e.g. `IsVisible`, `HasChildren`, `CanExecute`. These will give proper meaning to the properties.

Remember, good code is self-documented.

### Other Proper Practices

> Use Nullable Data Types whenever required.

Example:

```csharp
int index = 0; // Simple declaration of int
int? index = null; // Nullable data type declaration
```

---

> Use runtime constants over compile time constants.

Runtime constants are those being evaluated at the runtime and declared with the keyword `readonly`. On the other side, compile time constants are `static`, evaluated at the time of compilation and declared with the keyword `const`;

Example:

```csharp
public readonly string LOG_FILENAME = "app.log"; // Runtime constants
public const string LOG_FILENAME = "app.log"; // Compile time constants
```

So, what is the need to prefer `readonly` over `const` variables? Compile time constants (`const`) must be initialized at the time of declaration and can’t be changed later. Also, they are limited to only numbers and strings. The IL replaces the `const` variable with the value of it over the whole code and thus it is a bit faster. Whereas, the Runtime constants (`readonly`) are initialized in the constructor and can be changed at different initialization time. The IL references the `readonly` variable and not the original value. So, when you have some critical situation, use `const` to make the code run faster. When you need a reliable code, always prefer `readonly` variables.

---

> Use "is" and "as" operators while casting.

It's better to use `is` and `as` operator while casting, instead of explicit casting.

Example:

```csharp
var employee = (Employee)person;
```

In the code above, suppose your person is a `Customer` type and when you're converting it to `Employee` type, it will throw `Exception` and in that case, you have to handle it using `try-catch` block.

```csharp
// Check if the person is Employee type
if (person is Employee)
{
  // Convert person to Employee type
  employee = person as Employee;
}

// Check if the person is Customer type
if (person is Customer)
{
  // Conver person to Customer type
  customer = person as Customer;
}
```

In the code above, I do the checking before converting it to the right type. If it is unable to convert, it will return as `null` but will not throw any exception. So, from here we can check whether the converted value is `null`.

---

> Use string.Format() or StringBuilder for string concatenation.

It's because of better memory management! `string.Format()` will not create multiple objects and `StringBuilder` is an immutable object which will not create separate memory for each operation.

---

> Use Conditional Attributes when necessary.

Well, it's very helpful when you want to do something only for the debug version.

Example:

```csharp
private void printFirstname()
{
  string firstname = string.Empty;
  #if DEBUG
  firstname = getFirstname(); // In production, this method is never be called
  #endif
  Console.WriteLine(firstname);
}

// OR

[Conditional("DEBUG")]
[Conditional("TRACE")]
private void printFirstname()
{
  string firstname = getFirstname();
  Console.WriteLine(firstname);
}
```

---

> Use "0" (zero) as Default Value for Enum Value Types.

Example:

```csharp
public enum PersonType
{
  None = 0,
  Customer,
  Employee,
}

class Program
{
  static void Main(string[] args)
  {
    PersonType personType = new PersonType();
    Console.WriteLine(personType); // Will print "None"
  }
}
```

---

> Always prefer the foreach(...) loop.

The `foreach` statement is a variation of `do`, `while` or `for` loops. The best iteration code generation. The advantage is while looping through the Single Dimensional or Multi Dimensional array, you don't have to write multiline `for` statements. The compiler internally will generate that code. Thus, increases your productivity.

---

> Properly utilize try-catch-finally blocks.

If you write code that may throw some Exception, use the `try-catch` block for that piece of code to handle the exception. Unnecessary surrounding lines of code with `try-catch` will slow down your application. Use it only when required. Use the `finally` block to clean up any resources after the call, e.g. if you're doing any database call, close the connection in this block.

Example:

```csharp
void ReadFile(int index)
{
  // To run this code, substitute a valid path from your local machine
  string path = @"c:\users\public\test.txt";
  System.IO.StreamReader file = new System.IO.StreamReader(path);
  char[] buffer = new char[10];
  try
  {
    file.ReadBlock(buffer, index, buffer.Length);
  }
  catch (System.IO.IOException e)
  {
    Console.WriteLine("Error reading from {0}. Message = {1}", path, e.Message);
  }
  finally
  {
    if (file != null)
    {
      file.Close();
    }
  }
  // Do something with buffer...
}
```

---

> Catch only Exception that you can handle.

People always use the generic `Exception` class to catch any exception which neither good for your app nor for the system performance. You may use this generic `Exception` to catch for unknown exceptions. If you know that you code might throwing `NullReferenceException` or `ArgumentException`, use it specifically in order to easily handle the problem.

---

> Use IDisposable interface.

Use `IDisposable` interface to free all the resources from the memory. Once you implement `IDisposable` interface in your class, you will get a `Dispose()` method there. Write code there to free the resources.

Example:

```csharp
public class User : IDisposable
{
  public int id { get; protected set; }
  public string name { get; protected set; }
  public string pass { get; protected set; }

  public User(int userID)
  {
    id = userID;
  }
  public User(string Username, string Password)
  {
    name = Username;
    pass = Password;
  }

  // Other functions go here...

  public void Dispose()
  {
    Dispose(true);
    GC.SuppressFinalize(this);
  }

  protected virtual void Dispose(bool disposing)
  {
    if (disposing)
    {
      // free managed resources
    }
    // free native resources if there are any.
  }

}
```

If you're using `using(...) { ... }` block, it will call the `Dispose()` method automatically to free up the class resources. You will not have to call the `Dispose()` explicitly for the class.

---

> Split you logic in several small and simple methods.

If methods are too long, sometimes it's difficult to handle them. This is why you need to break them in separate methods and in future you may need to call one part, it will be easier to call rather than replicating the code. This is also easier to do unit testing for the small chunks rather than a big code. Based upon that, extract your code in small simple methods and call them from wherever you want. In general, a method should never be more than 10-15 lines long.

Example:

```csharp
// Assuming I'm going to calculate the force due to
// gravitational acting on two bodies of mass A kg and B kg
// separated by the distance X cm?
//
// Formula, F = (G * m1 * m2) / r^2
//

public double GetDividend(double gravityConstant, double mass1, double mass2)
{
  // Return G * m1 * m2
}

public double GetDivisor(double distance)
{
  // Convert distance from cm to m
  // Return distance with square
}

public double GetForce(double dividend, double divisor)
{
  // Return result of calculation = dividend / divisor
}

static void Main()
{
  var result = GetForce(GetDividend() / GetDivisor());
  Console.WriteLine(result.ToString());
}
```
