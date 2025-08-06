# DESIGN-PATTERNS
THE CATALOG OF DESIGN PATTERNS

# 🧠 The Catalog of Design Patterns

---

## 📘 01. Definition of Design Patterns

> In software engineering, **design patterns** are reusable solutions to common problems that occur in software design. They act as templates or blueprints that can be applied to real-world coding scenarios, improving maintainability and flexibility.

Learn more from:
- [Wikipedia – Design Patterns](https://en.wikipedia.org/wiki/Software_design_pattern)
- [Refactoring Guru – Design Patterns Overview](https://refactoring.guru/design-patterns)

---

## 🚀 02. Importance in Software Development

Design patterns are essential for building scalable and maintainable systems. They improve:

- 🧩 **Problem-solving**  
- 🤝 **Collaboration between developers**  
- ⚙️ **Code efficiency and reusability**  
- 📈 **Scalability**  
- 🔐 **Security**  
- 💡 **User experience**  
- 💰 **Economic impact (reducing time/cost)**

Further reading:
- [Microsoft – Design Patterns Overview](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures#design-patterns)
- [IBM – Why Design Patterns Matter](https://developer.ibm.com/articles/design-patterns-intro/)

---

## 🏗️ 03. Categories of Design Patterns

Design patterns fall under **three main categories**:

- **Creational** – Deal with object creation (e.g., Singleton, Factory Method)
- **Structural** – Deal with object composition (e.g., Adapter, Composite)
- **Behavioral** – Deal with object interaction (e.g., Observer, Strategy)

Learn more:
- [Refactoring Guru – Design Pattern Categories](https://refactoring.guru/design-patterns/catalog)

---

## 🔹 Singleton Pattern (Creational)

The Singleton pattern ensures that a class has only **one instance**, and provides a global point of access to it. Ideal for shared resources like configurations, logging, or caching.

🔗 Learn more: [Refactoring Guru – Singleton](https://refactoring.guru/design-patterns/singleton)

---

## 🔹 Factory Method Pattern (Creational)

The Factory Method pattern defines an **interface for object creation**, allowing subclasses to decide which class to instantiate. It promotes loose coupling and supports the Open/Closed Principle.

🔗 Learn more: [Refactoring Guru – Factory Method](https://refactoring.guru/design-patterns/factory-method)

---

## 🔹 Adapter Pattern (Structural)

The Adapter pattern enables collaboration between **incompatible interfaces** by converting one interface into another expected by the client. Commonly used when integrating legacy systems or third-party APIs.

🔗 Learn more: [Refactoring Guru – Adapter](https://refactoring.guru/design-patterns/adapter)

---

## 🔹 Observer Pattern (Behavioral)

The Observer pattern creates a **one-to-many relationship**, where changes to one object (Subject) automatically notify and update all dependent objects (Observers). It’s widely used in event-driven systems like UI frameworks or pub/sub systems.

🔗 Learn more: [Refactoring Guru – Observer](https://refactoring.guru/design-patterns/observer)

---

## 🧩 System-Level Architecture Flow

To understand how different design patterns fit into a real-world system, explore these resources:

- [Microsoft – Architecture Guide](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/)
- [Patterns.dev – Software Design Patterns](https://www.patterns.dev/posts/classic-design-patterns/)

---

## ✅ Bonus: Code Samples

Each pattern in this catalog includes sample implementations in:

- **C#**
- 
You can explore the `/patterns` folder in this repo for full project code per pattern.

---

## 📂 Contributing

Feel free to contribute with:
- More patterns (Builder, Composite, Command, Strategy, etc.)
- Real-world examples
- Additional languages (e.g., TypeScript, Kotlin)

---

## ⭐ License

MIT License © 2025

---


01. DEFINITION OF DESIGN PATTERNS
Design Patterns are standardized, reusable solutions to common design problems in software engineering. They serve as templates for solving recurring challenges in code architecture and design. Patterns allow developers to leverage proven approaches rather than reinventing solutions for every project.

02. IMPORTANCE IN SOFTWARE DEVELOPMENT
Design patterns are essential for:

User Experience: Enable predictable and maintainable interactions

Efficiency: Save development time through reuse

Problem-Solving: Offer tested, proven solutions

Collaboration: Provide a common vocabulary for developers

Scalability: Facilitate extensible system architecture

Economic Growth: Reduce cost and time to market

Security: Encourage secure architectural decisions

03. OVERVIEW OF CATEGORIES
Design Patterns are broadly divided into three main categories:

Category	Purpose	Examples
Creational	Simplify object creation and management	Singleton, Factory Method, Abstract Factory
Structural	Manage relationships between classes/objects	Adapter, Composite, Decorator
Behavioral	Manage algorithms, communication, and responsibilities	Observer, Strategy, Command

Detailed Explanation with Examples, UML, and Code
1. Creational Patterns
Singleton Pattern
Ensures a class has only one instance and provides a global access point.

UML Diagram for Singleton

Flow:
Check if instance exists.

If no, create new instance.

Return instance.

Sample Code:
C#:

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
Java:

java
Copy
Edit
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
Python:

python
Copy
Edit
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
        return cls._instance
Factory Method Pattern
Defines an interface for creating an object, but lets subclasses decide which class to instantiate.

UML Diagram for Factory Method

Flow:
Client calls factory method.

Subclass decides which product to create.

Sample Code:
C#:

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

public class ConcreteCreatorB : Creator
{
    public override Product FactoryMethod() => new ConcreteProductB();
}
2. Structural Patterns
Adapter Pattern
Allows incompatible interfaces to work together by wrapping one class with another.

UML Diagram for Adapter

Flow:
Client uses Target interface.

Adapter wraps Adaptee and converts calls.

Sample Code:
C#:

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
    }}

3. Behavioral Patterns
Observer Pattern
Defines a one-to-many dependency so that when one object changes state, all its dependents are notified.

UML Diagram for Observer

Flow:
Subject maintains a list of observers.

Observers register/unregister.

Subject notifies observers of state changes.

Sample Code:
C#:

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
    public ConcreteObserver(string name) { _name = name; }
    public void Update(string message)
    {
        Console.WriteLine($"{_name} received message: {message}");
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
    }}

Architecture Diagram - How Patterns Fit Together
Here is a high-level architecture flow showing how different design patterns support a scalable, maintainable system:


Creational patterns manage object lifecycle (Singleton manages shared state; Factory creates families of products).

Structural patterns form relationships between objects (Adapter for compatibility, Composite for hierarchical structures).

Behavioral patterns define communication (Observer for events, Command for actions).

🔹 Summary of Design Patterns
Singleton (Creational): Ensures that a class has only one instance and provides a global point of access to it. It is commonly used for configurations, logging, or shared resources.

Factory Method (Creational): Defines an interface for creating objects, but lets subclasses alter the type of objects that will be created. This pattern promotes loose coupling and enhances scalability.

Adapter (Structural): Allows objects with incompatible interfaces to collaborate by converting one interface into another that the client expects. Useful when integrating legacy or third-party code.

Observer (Behavioral): Establishes a one-to-many relationship between objects. When one object changes state, all its dependents are notified and updated automatically. Widely used in event handling systems.
