# How To Become A Senior Developer

## Full-Stack Plan for Senior Developer Mastery

# Backend Mastery 
# Advanced C# Mastery
## Object-Oriented Programming (OOP) in C#

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes to design software. OOP helps developers create modular, maintainable, and reusable code. C# is a powerful OOP language that provides four core principles of OOP:

1. **Encapsulation**
2. **Inheritance**
3. **Polymorphism**
4. **Abstraction**

This guide will cover each of these principles in detail, starting from the basics and advancing to complex concepts. We will also cover best practices, what to watch out for, and potential interview questions.

---

## Chapter 1: Encapsulation

### What is Encapsulation?

Encapsulation is the concept of wrapping data (fields) and methods (functions) together in a single unit (class). It restricts access to the internal details of a class and protects data integrity.

### Key Concepts

* Private Fields
* Public Methods
* Properties (Getters and Setters)
* Access Modifiers (private, public, protected, internal)

### Code Example

```csharp
public class BankAccount
{
    private decimal balance; // Private field (Encapsulated)

    // Public Method (Controlled Access)
    public void Deposit(decimal amount)
    {
        if (amount > 0)
        {
            balance += amount;
        }
    }

    // Public Method (Controlled Access)
    public void Withdraw(decimal amount)
    {
        if (amount > 0 && amount <= balance)
        {
            balance -= amount;
        }
    }

    // Public Property (Encapsulated)
    public decimal Balance
    {
        get { return balance; }
    }
}
```

### Why Use Encapsulation?

* Protects data integrity.
* Limits access to sensitive data.
* Allows controlled access through methods or properties.

### Best Practices

* Always keep fields private.
* Use properties (getters/setters) for controlled access.
* Use access modifiers appropriately (private, protected, public).

### Interview Questions

1. What is Encapsulation?
2. How do you enforce Encapsulation in C#?
3. Can Encapsulation be broken? How?

---

## Chapter 2: Inheritance

### What is Inheritance?

Inheritance is a mechanism where a new class (derived class) inherits the properties and methods of an existing class (base class).

### Key Concepts

* Base Class
* Derived Class
* "is-a" relationship
* Method Overriding
* Protected Access Modifier

### Code Example

```csharp
public class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

public class Dog : Animal // Inheriting from Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}
```

### Why Use Inheritance?

* Promotes code reusability.
* Establishes a natural hierarchy between classes.

### Best Practices

* Use inheritance only for "is-a" relationships.
* Avoid deep inheritance hierarchies.
* Prefer composition over inheritance where applicable.

### Interview Questions

1. What is Inheritance?
2. What is the difference between inheritance and composition?
3. How can you prevent a class from being inherited?

---

## Chapter 3: Polymorphism

### What is Polymorphism?

Polymorphism means "many forms." In C#, it allows methods to perform different tasks based on the object they are acting on.

### Key Concepts

* Method Overloading (Compile-Time Polymorphism)
* Method Overriding (Run-Time Polymorphism)
* Virtual, Override, and New Keywords

### Code Example

```csharp
public class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape.");
    }
}

public class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}
```

### Why Use Polymorphism?

* Supports flexibility and extensibility.
* Allows for code that can work with objects of different types.

### Best Practices

* Use polymorphism for method customization.
* Prefer interfaces over base class polymorphism when applicable.

### Interview Questions

1. What is Polymorphism?
2. What is the difference between Overloading and Overriding?
3. Can you override a private method in C#?

---

## Chapter 4: Abstraction

### What is Abstraction?

Abstraction means hiding the complexity and only exposing the essential details to the user.

### Key Concepts

* Abstract Classes
* Interfaces
* Abstract Methods

### Code Example

```csharp
public abstract class Vehicle
{
    public abstract void Start(); // Abstract Method
}

public class Car : Vehicle
{
    public override void Start()
    {
        Console.WriteLine("Car is starting.");
    }
}
```

### Why Use Abstraction?

* Simplifies complex logic.
* Promotes code flexibility.

### Best Practices

* Use abstraction for defining common behavior.
* Choose interfaces for behavior, abstract classes for shared code.

### Interview Questions

1. What is Abstraction?
2. What is the difference between an Interface and an Abstract Class?
3. Can you instantiate an Abstract Class?

---

## Conclusion

This guide provides a complete understanding of OOP principles in C#, including core concepts, detailed code examples, best practices, and common interview questions. Understanding these principles is critical for any C# developer, from beginner to advanced level.

# Advanced OOP Concepts in C# - Complete Guide

## Introduction

This guide is a continuation of the OOP Principles guide, focusing on advanced Object-Oriented Programming (OOP) concepts in C#. These concepts are essential for building scalable, maintainable, and robust software systems. We will cover the following advanced OOP topics:

1. **SOLID Principles**
2. **Design Patterns:**

   * Factory Pattern
   * Singleton Pattern
   * Strategy Pattern

Each topic will be explained in detail with:

* Clear definitions and purpose
* Code examples with explanations
* Best practices and common pitfalls
* Real-world use cases
* Interview questions and answers

---

## Chapter 1: SOLID Principles

### What are SOLID Principles?

SOLID is an acronym for five design principles that help create maintainable and scalable software systems:

* **S - Single Responsibility Principle (SRP)**
* **O - Open/Closed Principle (OCP)**
* **L - Liskov Substitution Principle (LSP)**
* **I - Interface Segregation Principle (ISP)**
* **D - Dependency Inversion Principle (DIP)**

### Detailed Explanation of Each Principle

#### 1. Single Responsibility Principle (SRP)

"A class should have only one reason to change."

#### Code Example:

```csharp
// Violating SRP
public class UserManager
{
    public void CreateUser(string username) { /* Logic to create user */ }
    public void SendWelcomeEmail(string email) { /* Logic to send email */ }
}

// Following SRP
public class UserCreator
{
    public void CreateUser(string username) { /* Logic to create user */ }
}

public class EmailService
{
    public void SendWelcomeEmail(string email) { /* Logic to send email */ }
}
```

#### Best Practices

* Ensure that each class has a single, well-defined responsibility.
* Separate logic into focused, cohesive classes.

#### Interview Questions

1. What is SRP?
2. Why is SRP important?
3. How would you identify a class violating SRP?

---

## Chapter 2: Factory Design Pattern

### What is the Factory Pattern?

The Factory Pattern is a creational design pattern that provides a method for creating objects without specifying the exact class type.

### Code Example

```csharp
public interface IProduct
{
    void Display();
}

public class ProductA : IProduct
{
    public void Display() => Console.WriteLine("Product A");
}

public class ProductB : IProduct
{
    public void Display() => Console.WriteLine("Product B");
}

public class ProductFactory
{
    public static IProduct CreateProduct(string type)
    {
        return type switch
        {
            "A" => new ProductA(),
            "B" => new ProductB(),
            _ => throw new ArgumentException("Invalid type")
        };
    }
}
```

### Why Use the Factory Pattern?

* Simplifies object creation logic.
* Allows switching between concrete implementations without modifying client code.

### Best Practices

* Use for complex object creation.
* Avoid using for simple objects (overkill).

### Interview Questions

1. What is the Factory Pattern?
2. When should you use it?
3. Can you implement Factory without using a switch statement?

---

## Chapter 3: Singleton Design Pattern

### What is the Singleton Pattern?

The Singleton Pattern is a creational design pattern that ensures only one instance of a class exists and provides global access to that instance.

### Code Example

```csharp
public class Singleton
{
    private static Singleton _instance;
    private static readonly object _lock = new object();

    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            lock (_lock)
            {
                if (_instance == null)
                {
                    _instance = new Singleton();
                }
                return _instance;
            }
        }
    }
}
```

### Why Use the Singleton Pattern?

* Ensures a single, consistent instance.
* Commonly used for logging, configuration, or caching.

### Best Practices

* Use thread-safe implementation.
* Avoid excessive use (can become a global state).

### Interview Questions

1. What is the Singleton Pattern?
2. How do you make a Singleton thread-safe?
3. Can you use a Lazy<T> for Singleton in C#?

---

## Chapter 4: Strategy Design Pattern

### What is the Strategy Pattern?

The Strategy Pattern is a behavioral design pattern that allows you to define a family of algorithms and make them interchangeable.

### Code Example

```csharp
public interface IPaymentStrategy
{
    void Pay(decimal amount);
}

public class CreditCardPayment : IPaymentStrategy
{
    public void Pay(decimal amount) => Console.WriteLine($"Paid {amount} with Credit Card.");
}

public class PayPalPayment : IPaymentStrategy
{
    public void Pay(decimal amount) => Console.WriteLine($"Paid {amount} with PayPal.");
}

public class PaymentProcessor
{
    private readonly IPaymentStrategy _paymentStrategy;

    public PaymentProcessor(IPaymentStrategy paymentStrategy)
    {
        _paymentStrategy = paymentStrategy;
    }

    public void ProcessPayment(decimal amount)
    {
        _paymentStrategy.Pay(amount);
    }
}
```

### Why Use the Strategy Pattern?

* Promotes flexibility and scalability.
* Allows different algorithms to be used interchangeably.

### Best Practices

* Use for algorithms with interchangeable logic.
* Favor composition over inheritance.

### Interview Questions

1. What is the Strategy Pattern?
2. What is the difference between Strategy and Factory Patterns?
3. Can you use Strategy without interfaces?

---

## Conclusion

This guide provides an in-depth understanding of advanced OOP concepts in C#, including SOLID principles and key design patterns (Factory, Singleton, and Strategy). Mastering these concepts is essential for designing robust, scalable software applications.

# Dependency Injection (DI) in ASP.NET Core - Complete Guide

## Introduction

Dependency Injection (DI) is a fundamental design pattern in ASP.NET Core, enabling the creation of loosely coupled, testable, and maintainable applications. This guide covers everything you need to know about Dependency Injection in ASP.NET Core, from basic concepts to advanced techniques.

---

## Chapter 1: Understanding Dependency Injection (DI)

### What is Dependency Injection?

Dependency Injection is a design pattern where objects (dependencies) are provided to a class, rather than the class creating them itself. It helps decouple the code and makes it more maintainable and testable.

### Key Concepts

* **Service**: A class that provides functionality.
* **Dependency**: An object required by another object.
* **Injection**: Providing the dependency to a class (via constructor, method, or property).

### Why Use Dependency Injection?

* Promotes Loose Coupling.
* Enhances Testability.
* Simplifies Configuration and Setup.

---

## Chapter 2: DI in ASP.NET Core

### How DI Works in ASP.NET Core

* ASP.NET Core has a built-in DI container (ServiceProvider).
* Services are registered in the `Startup.cs` or `Program.cs` file.
* Services can be registered with different lifetimes:

  * **Transient**: New instance for every request.
  * **Scoped**: One instance per request.
  * **Singleton**: One instance for the application lifetime.

### Code Example: Basic DI Setup

```csharp
// Program.cs in ASP.NET Core
var builder = WebApplication.CreateBuilder(args);

// Registering Services
builder.Services.AddTransient<IEmailService, EmailService>();
builder.Services.AddScoped<IUserService, UserService>();
builder.Services.AddSingleton<ILoggingService, LoggingService>();

var app = builder.Build();
app.Run();

// Service Interfaces and Implementations
public interface IEmailService
{
    void SendEmail(string message);
}

public class EmailService : IEmailService
{
    public void SendEmail(string message)
    {
        Console.WriteLine($"Email Sent: {message}");
    }
}
```

### Using DI in Controllers

```csharp
public class HomeController : Controller
{
    private readonly IEmailService _emailService;

    // Constructor Injection
    public HomeController(IEmailService emailService)
    {
        _emailService = emailService;
    }

    public IActionResult Index()
    {
        _emailService.SendEmail("Welcome to Dependency Injection!");
        return View();
    }
}
```

### Best Practices

* Prefer constructor injection over property or method injection.
* Register dependencies using the correct lifetime (Transient, Scoped, Singleton).
* Avoid using service locator (anti-pattern).

---

## Chapter 3: Advanced DI Techniques

### 1. Named or Multiple Implementations

* Multiple implementations can be registered and resolved using factory methods.

```csharp
builder.Services.AddTransient<IEmailService, SmtpEmailService>();
builder.Services.AddTransient<IEmailService, SendGridEmailService>();
```

### 2. Conditional Dependency Resolution

```csharp
builder.Services.AddTransient<IEmailService>(provider =>
{
    var config = provider.GetService<IConfiguration>();
    return config["EmailProvider"] == "Smtp"
        ? new SmtpEmailService()
        : new SendGridEmailService();
});
```

### 3. DI with Options Pattern

```csharp
builder.Services.Configure<MySettings>(builder.Configuration.GetSection("MySettings"));
```

### 4. DI with Factory Methods

```csharp
builder.Services.AddTransient<IProductService>(provider =>
{
    var isPremium = provider.GetService<IUserService>().IsPremiumUser();
    return isPremium ? new PremiumProductService() : new StandardProductService();
});
```

### 5. Service Provider Validation

* ASP.NET Core can validate service registrations at startup for correctness.

```csharp
builder.Services.AddControllers().AddControllersAsServices();
```

---

## Chapter 4: Common Pitfalls and Anti-Patterns

### 1. Service Locator Anti-Pattern

```csharp
// Bad Practice
var emailService = HttpContext.RequestServices.GetService<IEmailService>();
```

* This approach breaks the DI principle and should be avoided.

### 2. Overusing Singleton Services

* Avoid storing scoped services in singletons.

### 3. Constructor Over-Injection

* Avoid injecting too many dependencies into a single class.

---

## Chapter 5: DI Best Practices

* Use interfaces for services.
* Prefer constructor injection for mandatory dependencies.
* Avoid using service locator.
* Use the correct service lifetime (Transient, Scoped, Singleton).
* Validate DI setup at startup.

---

## Chapter 6: Interview Questions

1. What is Dependency Injection?
2. What are the different DI lifetimes in ASP.NET Core?
3. What is the Service Locator Anti-Pattern?
4. Can you explain Constructor Injection vs. Property Injection?
5. How can you implement multiple service implementations?
6. How do you use the Options pattern with DI?

---

## Conclusion

This guide provides a complete understanding of Dependency Injection (DI) in ASP.NET Core, from basic to advanced techniques. Mastering DI is essential for building scalable, maintainable, and testable ASP.NET Core applications.

# Memory Management in C# - Complete Guide

## Introduction

Memory management is a critical aspect of developing efficient and robust applications in C#. Understanding how memory is allocated, managed, and released can significantly improve application performance. This guide covers everything you need to know about memory management in C#, including:

1. **Garbage Collection (GC)**
2. **IDisposable and Dispose Pattern**
3. **Value Types vs. Reference Types**

We will explore each topic in detail with explanations, best practices, code examples, and common interview questions.

---

## Chapter 1: Garbage Collection (GC)

### What is Garbage Collection?

Garbage Collection (GC) is an automatic memory management feature in .NET that automatically frees unused objects from memory, preventing memory leaks.

### How Garbage Collection Works

* **Generational Garbage Collection:**

  * Generation 0: Short-lived objects (frequent collections).
  * Generation 1: Medium-lived objects (less frequent collections).
  * Generation 2: Long-lived objects (rarely collected).
* **GC Phases:**

  1. Mark: Identifies live objects.
  2. Sweep: Releases memory of dead objects.
  3. Compact: Optimizes memory layout.

### Code Example

```csharp
class Program
{
    static void Main()
    {
        for (int i = 0; i < 10000; i++)
        {
            var data = new byte[1024]; // Allocating memory
        }

        // Forcing GC Collection (Not recommended in production)
        GC.Collect();
        GC.WaitForPendingFinalizers();

        Console.WriteLine("Garbage Collection Complete.");
    }
}
```

### Best Practices

* Avoid manually calling `GC.Collect()`.
* Minimize object allocations inside loops.
* Use pooling for frequently used objects.

### Interview Questions

1. What is Garbage Collection?
2. What are the GC generations?
3. How does GC determine which objects to collect?

---

## Chapter 2: IDisposable and Dispose Pattern

### What is IDisposable?

IDisposable is an interface that defines a `Dispose()` method for releasing unmanaged resources (like file handles, database connections, etc.).

### Why Use IDisposable?

* To release unmanaged resources explicitly.
* To prevent resource leaks.

### Code Example

```csharp
public class FileManager : IDisposable
{
    private FileStream _fileStream;

    public FileManager(string filePath)
    {
        _fileStream = new FileStream(filePath, FileMode.Open);
    }

    public void ReadFile()
    {
        Console.WriteLine("Reading file...");
    }

    // Implementing Dispose
    public void Dispose()
    {
        _fileStream?.Dispose();
        Console.WriteLine("File stream disposed.");
    }
}

// Using IDisposable
using (var fileManager = new FileManager("example.txt"))
{
    fileManager.ReadFile();
}
```

### The Dispose Pattern (Advanced)

* For complex classes, use a more robust Dispose pattern with a `finalizer`.

```csharp
public class ResourceManager : IDisposable
{
    private bool _disposed = false;

    ~ResourceManager() // Finalizer
    {
        Dispose(false);
    }

    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    protected virtual void Dispose(bool disposing)
    {
        if (!_disposed)
        {
            if (disposing)
            {
                // Release managed resources
            }
            // Release unmanaged resources
            _disposed = true;
        }
    }
}
```

### Best Practices

* Use `using` or `await using` blocks for IDisposable objects.
* Always implement `Dispose` when using unmanaged resources.
* Avoid finalizers unless necessary.

### Interview Questions

1. What is IDisposable?
2. What is the Dispose Pattern?
3. What is the difference between Dispose() and Finalize()?

---

## Chapter 3: Value Types vs Reference Types

### What are Value Types and Reference Types?

* **Value Types:** Stored on the stack. Copies are created when assigned.

  * Examples: int, double, struct, bool.

* **Reference Types:** Stored on the heap. A reference (pointer) is created.

  * Examples: class, string, array, object.

### Code Example

```csharp
// Value Type Example
int a = 10;
int b = a;
b = 20;
Console.WriteLine(a); // 10

// Reference Type Example
class Person
{
    public string Name { get; set; }
}

Person person1 = new Person { Name = "John" };
Person person2 = person1;
person2.Name = "Doe";
Console.WriteLine(person1.Name); // Doe
```

### Best Practices

* Use value types for small, simple data.
* Use reference types for complex objects.
* Understand the difference for performance optimization.

### Interview Questions

1. What are Value Types and Reference Types?
2. How are Value Types and Reference Types stored in memory?
3. Can you create a custom Value Type?

---

## Chapter 4: Best Practices and Common Pitfalls

### Best Practices

* Avoid unnecessary object allocations.
* Use the `using` statement for IDisposable objects.
* Use value types for small, immutable data.
* Use reference types for complex objects.

### Common Pitfalls

* Misusing IDisposable without proper Dispose pattern.
* Excessive object allocations (causing GC overhead).
* Confusion between value and reference types.

---

## Chapter 5: Interview Questions

1. What is Garbage Collection in C#?
2. What is the difference between Dispose() and Finalize()?
3. What are Value Types and Reference Types?
4. What is the Dispose Pattern?
5. When should you use IDisposable?
6. How can you optimize memory management in C#?

---

## Conclusion

This guide provides a complete understanding of Memory Management in C#, including Garbage Collection, IDisposable, and the differences between Value Types and Reference Types. Mastering these concepts is essential for building high-performance .NET applications.

