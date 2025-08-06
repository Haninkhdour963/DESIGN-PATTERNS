# DESIGN-PATTERNS
🧠 DESIGN PATTERNS CATALOG
Welcome to the Design Patterns Catalog, a curated guide to fundamental design patterns in software engineering, with definitions, benefits, code samples, and UML insights. This repository is aimed at helping developers understand, implement, and apply design patterns effectively to build scalable, maintainable, and elegant software systems.

📘 What Are Design Patterns?
In software engineering, design patterns are standardized, reusable solutions to common problems that arise in software design. Rather than solving problems from scratch, developers can rely on these proven templates to improve code quality, consistency, and maintainability.

Learn more:
🔗 Wikipedia – Design Patterns
🔗 Refactoring Guru – Design Patterns Overview

🚀 Why Use Design Patterns?
Design patterns play a critical role in modern software development by promoting:

💡 Problem-solving: Leverage tried-and-tested solutions.

⚙️ Code reusability: Reduce duplication and boilerplate.

📈 Scalability: Facilitate the design of extensible systems.

🔐 Security: Encourage safe architectural decisions.

🤝 Team collaboration: Provide a shared vocabulary for developers.

⏱️ Efficiency: Accelerate development time.

🧠 User experience: Enhance predictability and usability.

💰 Cost-effectiveness: Reduce time-to-market and maintenance costs.

Learn more:
🔗 Microsoft – Design Patterns
🔗 IBM – Why Design Patterns Matter

🏗️ Categories of Design Patterns
Design patterns are typically grouped into three main categories:

Creational Patterns: Handle object creation mechanisms.

Structural Patterns: Focus on object composition and relationships.

Behavioral Patterns: Define communication between objects.

Explore more:
🔗 Refactoring Guru – Pattern Categories

🔹 Key Patterns Covered
✅ Singleton Pattern (Creational)
Ensures a class has only one instance and provides a global access point.
Common use cases: Configuration management, logging, caching.

C# Example:

csharp
Copy
Edit
public class Singleton
{
    private static Singleton _instance;
    private static readonly object _lock = new();

    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            lock (_lock)
            {
                if (_instance == null)
                    _instance = new Singleton();
                return _instance;
            }
        }
    }
}
🔗 Refactoring Guru – Singleton

✅ Factory Method Pattern (Creational)
Defines an interface for object creation, letting subclasses decide which class to instantiate.
Ideal for decoupling object creation from usage.

C# Example:

csharp
Copy
Edit
public abstract class Product { }
public class ConcreteProductA : Product { }
public class ConcreteProductB : Product { }

public abstract class Creator
{
    public abstract Product FactoryMethod();
}

public class ConcreteCreatorA : Creator
{
    public override Product FactoryMethod() => new ConcreteProductA();
}
🔗 Refactoring Guru – Factory Method

✅ Adapter Pattern (Structural)
Allows incompatible interfaces to work together by wrapping an existing class with a new interface.

C# Example:

csharp
Copy
Edit
public interface ITarget
{
    void Request();
}

public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Called SpecificRequest()");
    }
}

public class Adapter : ITarget
{
    private readonly Adaptee _adaptee;

    public Adapter(Adaptee adaptee)
    {
        _adaptee = adaptee;
    }

    public void Request()
    {
        _adaptee.SpecificRequest();
    }
}
🔗 Refactoring Guru – Adapter

✅ Observer Pattern (Behavioral)
Defines a one-to-many dependency so that when one object (Subject) changes state, all dependents (Observers) are notified automatically.

C# Example:

csharp
Copy
Edit
public interface IObserver
{
    void Update(string message);
}

public class ConcreteObserver : IObserver
{
    private string _name;
    public ConcreteObserver(string name) => _name = name;

    public void Update(string message)
    {
        Console.WriteLine($"{_name} received: {message}");
    }
}

public class Subject
{
    private List<IObserver> _observers = new();

    public void Attach(IObserver observer) => _observers.Add(observer);
    public void Detach(IObserver observer) => _observers.Remove(observer);

    public void Notify(string message)
    {
        foreach (var observer in _observers)
            observer.Update(message);
    }
}
🔗 Refactoring Guru – Observer

🧩 System Architecture & Pattern Flow
Design patterns fit naturally into real-world architecture. For example:

Singleton handles shared configurations or service instances.

Factory Method supports modular, pluggable architectures.

Adapter enables legacy system integration or third-party interoperability.

Observer powers reactive UIs, pub/sub systems, and event-driven designs.

Architecture resources:
🔗 Microsoft Architecture Guide
🔗 Patterns.dev – Design Patterns

📂 Code Samples
Each design pattern is implemented in C#, located in the /patterns folder of this repository. More language implementations are welcome!

🤝 Contributing
You’re welcome to contribute by:

Adding more patterns (e.g., Builder, Strategy, Command)

Providing real-world use cases

Implementing examples in other languages (e.g., Java, Python, TypeScript)

📜 License

© 2025 Haninkhdour963
