---
layout: post
title: Simple Singleton Pattern Using .NET 4's Lazy Type
description: This singleton pattern is simple and performs well, best used with time-consuming operation class.
keywords: singleton pattern, .net 4, laziness, lambda expression
---

Nowadays, most of the Microsoft .NET based applications are using .NET 4 or higher. When talking about Singleton pattern, this way of implementation is my favorite - using the `System.Lazy<T>` type.

All you need to do is pass a delegate to the constructor which calls the Single constructor, which is done most easily with a lambda expression.

Let say I have a class called `SayHello.cs` with the Singleton pattern:

```csharp
using System;

namespace SingletonExample
{
    class SayHello
    {
        private static readonly Lazy<SayHello> lazy = new Lazy<SayHello>(() => new SayHello());
        public static SayHello Instance { get { return lazy.Value; } }

        SayHello()
        {
        }

        public void Test()
        {
            Console.WriteLine("Hello hello hello!");
        }
    }
}
```

And here my main program that will execute a function from `SayHello.cs` class:

```csharp
using System;

namespace SingletonExample
{
    class Program
    {
        static void Main(string[] args)
        {
            SayHello.Instance.Test();

            Console.ReadLine();
        }
    }
}
```

Here's the output:

![SingletonExample](http://i.imgur.com/Vnbsea3.png)

This singleton pattern is simple and performs well, best used with time-consuming operation class.
