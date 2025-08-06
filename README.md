# DESIGN-PATTERNS
THE CATALOG OF DESIGN PATTERNS
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

Summary Table for Your README
Pattern	Category	Purpose	UML Diagram Link
Singleton	Creational	Single instance globally accessible	
Factory Method	Creational	Define interface for object creation	
Adapter	Structural	Allow incompatible interfaces to work	
Observer	Behavioral	One-to-many notification	
