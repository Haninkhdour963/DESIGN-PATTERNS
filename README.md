# DESIGN-PATTERNS
THE CATALOG OF DESIGN PATTERNS

01 - DEFINITION OF DESIGN PATTERNS
Design Patterns in software engineering are standardized reusable solutions to common problems faced during software design. Instead of reinventing solutions for recurring design issues, patterns provide templates or blueprints that can be adapted for specific problems.

02 - IMPORTANCE IN SOFTWARE DEVELOPMENT
Design Patterns bring numerous benefits:

User Experience: Provide stable, tested ways to solve UX-related problems like event handling, UI updates.

Efficiency: Accelerate development by reusing proven solutions.

Problem-Solving: Offer solutions to known design problems reducing bugs and improving maintainability.

Collaboration: Common language shared among developers improving communication.

Scalability: Support designs that scale better under new requirements.

Economic Growth: Reduces development time and cost.

Security: Patterns promote safer, more robust code design.

03 - OVERVIEW OF CATEGORIES
Design Patterns fall into 3 main categories:

Category	Description	Examples
Creational	Patterns about object creation	Singleton, Factory Method, Abstract Factory
Structural	Patterns about object composition	Adapter, Composite, Decorator
Behavioral	Patterns about communication between objects	Observer, Strategy, Command

DETAILED PATTERN ANALYSIS
1. CREATIONAL PATTERNS
a. Singleton Pattern
Purpose: Ensure a class has only one instance and provide a global point of access to it.

UML Diagram (Text Description)
pgsql
Copy
Edit
+-----------------+
|   Singleton     |
+-----------------+
| - instance      |  <<static>>
+-----------------+
| + getInstance() |
+-----------------+
The class holds a private static instance of itself.

Constructor is private.

Public static method returns the instance, creating it if none exists.

Flowchart
Call getInstance()

Check if instance exists:

If yes, return it

If no, create new instance and return it

Sample Code
C#

csharp
Copy
Edit
public sealed class Singleton
{
    private static Singleton? _instance = null;
    private static readonly object _lock = new();

    private Singleton() { }

    public static Singleton GetInstance()
    {
        if (_instance == null)
        {
            lock (_lock)
            {
                if (_instance == null)
                    _instance = new Singleton();
            }
        }
        return _instance;
    }
}
Java

java
Copy
Edit
public class Singleton {
    private static volatile Singleton instance;
    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized(Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
Python

python
Copy
Edit
class Singleton:
    _instance = None

    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
        return cls._instance
b. Factory Method Pattern
Purpose: Define an interface for creating an object but let subclasses decide which class to instantiate.

UML Diagram (Text)
diff
Copy
Edit
+----------------+
| Creator        |
+----------------+
| + factoryMethod() : Product |
+----------------+
         ▲
         |
+------------------+
| ConcreteCreator  |
+------------------+
| + factoryMethod() |
+------------------+

+----------------+
| Product        |
+----------------+
         ▲
         |
+------------------+
| ConcreteProduct  |
+------------------+
Flowchart
Client calls factoryMethod

Subclass decides which concrete product to instantiate

Returns the product interface

Sample Code
C#

csharp
Copy
Edit
// Product interface
public interface IProduct
{
    void Operation();
}

// Concrete Product
public class ConcreteProductA : IProduct
{
    public void Operation() => Console.WriteLine("ConcreteProductA operation.");
}

// Creator
public abstract class Creator
{
    public abstract IProduct FactoryMethod();
    
    public void SomeOperation()
    {
        var product = FactoryMethod();
        product.Operation();
    }
}

// Concrete Creator
public class ConcreteCreatorA : Creator
{
    public override IProduct FactoryMethod()
    {
        return new ConcreteProductA();
    }
}
Java

java
Copy
Edit
interface Product {
    void operation();
}

class ConcreteProductA implements Product {
    public void operation() {
        System.out.println("ConcreteProductA operation.");
    }
}

abstract class Creator {
    public abstract Product factoryMethod();

    public void someOperation() {
        Product product = factoryMethod();
        product.operation();
    }
}

class ConcreteCreatorA extends Creator {
    public Product factoryMethod() {
        return new ConcreteProductA();
    }
}
2. STRUCTURAL PATTERNS
a. Adapter Pattern
Purpose: Convert the interface of a class into another interface clients expect. It allows incompatible interfaces to work together.

UML Diagram (Text)
lua
Copy
Edit
+----------+      +------------------+
| Target   |      | Adaptee          |
+----------+      +------------------+
| Request()|<-----| SpecificRequest() |
+----------+      +------------------+
       ▲
       |
+-------------+
| Adapter     |
+-------------+
| Request()   |
+-------------+
Flowchart
Client calls Request() on Target interface

Adapter translates to SpecificRequest() of Adaptee

Returns result back to client

Sample Code
C#

csharp
Copy
Edit
// Target interface
public interface ITarget
{
    void Request();
}

// Adaptee class
public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Adaptee's specific request.");
    }
}

// Adapter class
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
Python

python
Copy
Edit
class Target:
    def request(self):
        pass

class Adaptee:
    def specific_request(self):
        print("Specific request from Adaptee")

class Adapter(Target):
    def __init__(self, adaptee):
        self.adaptee = adaptee

    def request(self):
        self.adaptee.specific_request()
3. BEHAVIORAL PATTERNS
a. Observer Pattern
Purpose: Define a one-to-many dependency so that when one object changes state, all its dependents are notified and updated automatically.

UML Diagram (Text)
pgsql
Copy
Edit
+----------+      1        *       +-----------+
| Subject  |----------------------| Observer  |
+----------+                      +-----------+
| +attach()|                      | +update() |
| +detach()|                      +-----------+
| +notify()|
+----------+
Flowchart
Subject changes state

Calls notify()

Each observer is updated via update() method

Sample Code
Java

java
Copy
Edit
import java.util.*;

interface Observer {
    void update(String state);
}

class ConcreteObserver implements Observer {
    private String name;
    public ConcreteObserver(String name) {
        this.name = name;
    }

    public void update(String state) {
        System.out.println(name + " received update: " + state);
    }
}

class Subject {
    private List<Observer> observers = new ArrayList<>();
    private String state;

    public void attach(Observer observer) {
        observers.add(observer);
    }

    public void detach(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers() {
        for (Observer o : observers) {
            o.update(state);
        }
    }

    public void setState(String newState) {
        state = newState;
        notifyObservers();
    }
}
ARCHITECTURE LEVEL EXAMPLE: USING DESIGN PATTERNS IN A MODULAR SYSTEM
Imagine a payment processing system with multiple payment gateways (e.g., PayPal, Stripe).

Use Factory Method to instantiate the correct payment gateway object based on user selection.

Use Adapter to unify different gateway interfaces into a common interface.

Use Observer to notify different system parts (UI, logs, analytics) when payment state changes.

Use Singleton to manage configuration/settings for the payment system globally.

