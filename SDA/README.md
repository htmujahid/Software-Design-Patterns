_Software Design and Architecture_

-   [Introduction](#introduction)
-   [Software Design Process](#object-oriented-design)
-   [Software Design Process](#software-design-process)
    -   [Cohesion](#cohesion)
    -   [Coupling](#coupling)
-   [Software Design Principles](#software-design-principles)
    -   [Single Responsibility Principle](#single-responsibility-principle)
    -   [Open-Close Principle](#open-close-principle)
    -   [Liskov Substitution Principle](#liskov-substitution-principle)
    -   [Interface Segregation Principle](#interface-segregation-principle)
    -   [Dependency Inversion Principle](#dependency-inversion-principle)
    -   [Package Level Software Design Principle](#package-level-software-design-principles)
    -   [Release Reuse Equibalency Principle](#release-reuse-equibalency-principle)
    -   [Commono Closure Principle](#common-clousure-principle)
    -   [Common Reuse Principe](#common-reuse-principle)
    -   [Acyclic Dependencies Principe](#acyclic-dependencies-principle)
    -   [Stable Depencies Principle](#stable-dependcies-principle)
-   [Software Design Patterns](#software-design-patterns)
    -   [Creational Design Patterns](#creational-design-patterns)
        -   [Singleton Pattern](#singleton-pattern)
        -   [Facade Pattern](#facade-pattern)
        -   [Abstract Factory Pattern](#abstract-factory-pattern)
        -   [Builder Pattern](#builder-pattern)
        -   [Prototype Pattern](#prototype-pattern)
        -   [Object Pool Pattern](#object-pool-pattern)
    -   [Structural Design Patterns](#structural-design-patterns)
        -   [Adapter Pattern](#adapter-pattern)
        -   [Bridge Pattern](#bridge-pattern)
        -   [Composite Pattern](#composite-pattern)
        -   [Decorator Pattern](#decorator-pattern)
        -   [Facade Pattern](#facade-pattern)
        -   [Flyweight Pattern](#flyweight-pattern)
        -   [Proxy Pattern](#proxy-pattern))
    -   [Behavioral Design Patterns](#behavioral-design-patterns)
        -   [Chain of Responsibility Pattern](#chain-of-responsiblity-pattern)
        -   [Command Pattern](#command-pattern)
        -   [Observer Pattern](#observer-pattern)
        -   [Iterator Pattern](#iterator-pattern)
        -   [State Pattern](#state-pattern)
        -   [Visitor Pattern](#visitor-pattern)
        -   [Mediator Pattern](#mediator-pattern)
        -   [Memento Pattern](#memento-pattern)
        -   [Strategy Pattern](#strategy-pattern)
        -   [Template Method Pattern](#template-metohd-pattern)
-   [Software Architectural Patterns](#software-architectural-patterns)
    -   [Model View Controller Architecture](#model-view-controller-architecture)
    -   [Layered Architectured](#layered-architecture)
    -   [Enterprise Architecture](#enterprise-architecture)
    -   [Business Architecture](#business-architecture)
    -   [Information System Architecture](#information-system-architecture)
    -   [Application Architecture and Data Architecture](#application-architecture--data-architecture)

# Introduction

Software design refers to the process of creating a plan for a software application's structure, functionality, and features. It includes determining the software's requirements, identifying the design patterns to be used, and creating a detailed design specification.

Software architecture refers to the overall structure and organization of a software application, including its components, modules, and their interactions. It involves designing a high-level view of the software application's system, which includes defining the software's interfaces, data flows, and communication patterns.

Software design and architecture are crucial in ensuring that software applications are scalable, maintainable, and reliable. They help software developers create software applications that are efficient, secure, and meet the needs of end-users.

# Object Oriented Design

Object-oriented programming (OOP) is a programming paradigm that revolves around the concept of objects, which are instances of classes that encapsulate data and behavior. OOP emphasizes code organization, reuse, and maintainability, making it a popular choice for developing large-scale applications.

In OOP, classes define the blueprint for creating objects, and objects are created from these classes using the new operator. A class consists of data members, which represent the object's attributes or state, and member functions, which represent the object's behavior or methods.

OOP has four main principles: encapsulation, inheritance, polymorphism, and abstraction.

-   Encapsulation: Encapsulation is the practice of hiding the implementation details of a class and exposing only the necessary interface to the user. This allows for better code organization, improves code maintainability, and reduces the risk of accidental modification.

-   Inheritance: Inheritance is the process of creating new classes that inherit properties and behaviors from existing classes. This allows for code reuse and enables the creation of more specialized classes.

-   Polymorphism: Polymorphism allows objects of different classes to be treated as if they were of the same class, enabling code to be written that can work with objects in a more generic way. Polymorphism can be achieved through method overriding and method overloading.

-   Abstraction: Abstraction is the practice of focusing on the essential features of an object and ignoring its non-essential details. This allows for a simpler and more maintainable codebase.

One of the main advantages of OOP is that it enables modular programming, allowing developers to break down large problems into smaller, more manageable ones. Additionally, OOP allows for code reuse, as classes and objects can be easily used in multiple parts of an application.

# Software Design Process

The software design process is a series of steps that software developers follow to create a detailed plan for building a software application. It typically involves analyzing requirements, creating a high-level design, refining the design through iterations, and creating a detailed design specification that guides the implementation process. The software design process also includes reviewing and testing the design to ensure that it meets the software's functional and non-functional requirements.

## Cohesion

Cohesion refers to the degree to which the elements within a module or component work together to achieve a single purpose. In other words, it measures how well the responsibilities of a module are aligned and how focused its functionality is. A highly cohesive module is one that has a single, well-defined purpose and contains related functions.

```cpp
// A class with high cohesion, containing methods that are all related to mathematical operations

class MathOperations {
public:
    double square(double x) {
        return x * x;
    }

    double cube(double x) {
        return x * x * x;
    }

    double power(double x, int n) {
        double result = 1;
        for (int i = 0; i < n; i++) {
            result *= x;
        }
        return result;
    }
};
```

In the above example, all the methods within the MathOperations class are related to mathematical operations, and the class has a clear and well-defined purpose.

## Coupling

Coupling, on the other hand, refers to the degree to which different modules or components depend on each other. Low coupling indicates that modules are loosely connected, and changes in one module do not have a significant impact on other modules. High coupling, on the other hand, indicates that modules are tightly connected, and changes in one module can have a significant impact on other modules.

```cpp
// A class with high coupling, where a change in one class requires changes in another class

class Customer {
public:
    Customer(string name, string email) : name(name), email(email) {}
    string getName() {
        return name;
    }
    string getEmail() {
        return email;
    }
private:
    string name;
    string email;
};

class Order {
public:
    Order(Customer customer, vector<string> items) : customer(customer), items(items) {}
    string getCustomerName() {
        return customer.getName();
    }
    string getCustomerEmail() {
        return customer.getEmail();
    }
private:
    Customer customer;
    vector<string> items;
};
```

In the above example, the Order class is tightly coupled to the Customer class. If the Customer class changes, it could potentially affect the Order class, which is not ideal. A better approach would be to use a simpler data structure like a struct to represent the customer, so that the Order class is less dependent on the Customer class.

Designing software components with high cohesion and low coupling is important to create software that is modular, flexible, and easy to maintain. Therefore, understanding and managing cohesion and coupling is an important part of the software design process.

# Software Design Principles

Software design principles are guidelines or rules that software designers follow to create software that is well-structured, maintainable, and extensible. These principles are based on best practices and lessons learned from experience in software development.

## Single Responsibility Principle

The SRP states that a class should have only one responsibility or reason to change. This means that a class should only have one job, and if that job changes, the class should be modified accordingly. For example:

```cpp
class Shape {
public:
    virtual double area() const = 0;
};

class Circle : public Shape {
public:
    double area() const override { /_ ... _/ }
};

class Rectangle : public Shape {
public:
    double area() const override { /_ ... _/ }
};
```

In this example, the Shape class has a single responsibility: to define a shape with an area. The Circle and Rectangle classes inherit from Shape and implement the area calculation specific to their shape.

## Open-Close Principle

The OCP states that software entities should be open for extension, but closed for modification. This means that existing code should not be modified to add new features, but instead should be extended through inheritance, composition, or other means. For example:

```cpp
class Logger {
public:
    virtual void log(const std::string& message) = 0;
};

class ConsoleLogger : public Logger {
public:
    void log(const std::string& message) override {
        std::cout << message << std::endl;
    }
};

class FileLogger : public Logger {
public:
    void log(const std::string& message) override {
        std::ofstream file("log.txt");
        file << message << std::endl;
    }
};
```

In this example, the Logger class defines the interface for logging messages, while the ConsoleLogger and FileLogger classes implement that interface for specific output destinations. If a new output destination is needed (e.g. a network log), a new class can be created without modifying the existing code.

## Liskov Substitution Principle

The LSP states that subtypes should be substitutable for their base types, without affecting the correctness of the program. This means that derived classes should not break the behavior of the base class. For example:

```cpp
class Animal {
public:
    virtual void makeSound() const = 0;
};

class Cat : public Animal {
public:
    void makeSound() const override {
        std::cout << "Meow!" << std::endl;
    }
};

class Dog : public Animal {
public:
    void makeSound() const override {
        std::cout << "Woof!" << std::endl;
    }
};

void makeAnimalSound(const Animal& animal) {
    animal.makeSound();
}

int main() {
    Cat cat;
    Dog dog;
    makeAnimalSound(cat);
    makeAnimalSound(dog);
}
```

In this example, the Animal class defines the interface for all animals to make a sound. The Cat and Dog classes implement that interface for specific animals, and can be substituted for Animal without affecting the correctness of the program.

## Interface Segregation Principle

The ISP states that a client should not be forced to depend on methods it does not use. This means that interfaces should be designed to be as small as possible, with only the methods needed by the client. For example:

```cpp
class Printer {
public:
    virtual void print() = 0;
};

class Scanner {
public:
    virtual void scan() = 0;
};

class Copier : public Printer, public Scanner {
public:
    void print() override { /* ... */ }
    void scan() override { /* ... */ }
};
```

In this example, the Printer and Scanner classes define separate interfaces for printing and scanning, respectively. The Copier class implements both interfaces, and can be used wherever a Printer or Scanner is required.

## Dependency Inversion Principle

The DIP states that high-level modules should not depend on low-level modules, but both should depend on abstractions. This means that dependencies should be abstracted and injected, rather than hardcoded in the code. For example:

```cpp
class Database {
public:
    virtual void save(const std::string& data) = 0;
};

class FileDatabase : public Database {
public:
    void save(const std::string& data) override {
        std::ofstream file("data.txt");
        file << data << std::endl;
    }
};

class NetworkDatabase : public Database {
public:
    void save(const std::string& data) override {
    // send data over the network
}
};

class DataManager {
public:
    DataManager(Database& database) : database*(database) {}
    void saveData(const std::string& data) {
        database*.save(data);
    }
private:
    Database& database\_;
};

int main() {
    FileDatabase fileDatabase;
    DataManager dataManager(fileDatabase);
    dataManager.saveData("data");
}
```

In this example, the Database class defines the interface for saving data, while the FileDatabase and NetworkDatabase classes implement that interface for specific storage types. The DataManager class depends on the Database abstraction, which is injected into the constructor. This allows different storage types to be used without changing the DataManager code.

## Package Level Software Design principles

Here are some of the most important package level design principles:

-   Cohesion: Packages should contain related functionality and have a clear and well-defined purpose.

-   Coupling: Packages should have low coupling, meaning that they should be loosely connected to other packages. This reduces the impact of changes in one package on other packages.

-   Encapsulation: Packages should encapsulate implementation details, meaning that the package's internal structure and behavior should be hidden from other packages.

-   Abstraction: Packages should be designed to be abstract and generic, which makes them easier to reuse in other projects.

-   Modularity: Packages should be modular, meaning that they can be easily added, removed, or replaced without affecting the rest of the system.

-   Stability: Packages should be stable, meaning that their interfaces and behavior should remain relatively unchanged over time.

By following these principles, software developers can create packages that are easy to understand, maintain, and extend. This, in turn, leads to better software quality, higher productivity, and lower maintenance costs.

## Release Reuse Equibalency Principle

The Release Reuse Equivalency Principle (REP) is a software design principle that states that the cost of creating and maintaining reusable software components should be roughly equivalent to the cost of creating and maintaining the same functionality from scratch for a specific application.

The principle is based on the idea that the time and effort required to design, develop, test, document, and maintain a reusable software component can be significant, and may not be worth the investment if the component is not likely to be reused in multiple applications.

According to the REP, the decision to create a reusable software component should be based on the expected frequency and scope of reuse, as well as the expected cost of developing and maintaining the component. If the expected reuse is low and the cost of creating a reusable component is high, it may be more cost-effective to simply implement the functionality from scratch for each application.

In practice, the REP can help software designers make informed decisions about whether to create reusable software components, and can help ensure that the costs and benefits of reusability are carefully considered in the design process.

## Common Clousure Principle

The Common Closure Principle (CCP) is a software design principle that states that classes and modules should be designed and grouped together based on the types of changes that are likely to affect them.

According to CCP, classes and modules that are likely to be changed together should be grouped together, while classes and modules that are likely to be changed independently should be separated. The principle is based on the idea that changes to a software system should be localized and limited in scope, and that this can be achieved by designing modules that are cohesive and loosely coupled.

In practice, the CCP can be applied in several ways, including:

Grouping together classes that are part of the same feature or functionality, and that are likely to be modified together in response to changes in the requirements or use cases.
Separating classes that have different responsibilities or concerns, and that are likely to be modified independently of each other.
Designing modules with clear and well-defined boundaries, and ensuring that changes within a module do not affect other modules in the system.
By applying the CCP, software designers can create software systems that are easier to maintain, modify, and extend over time, and that are less likely to be affected by unintended consequences of changes to the system.

## Common Reuse Principle

The Common Reuse Principle (CRP) is a software design principle that states that classes and modules should be designed and grouped together based on the types of functionality that they provide, rather than the types of changes that are likely to affect them.

According to the CRP, classes and modules that provide similar or related functionality should be grouped together and designed for reuse, so that they can be shared and reused across multiple applications. The principle is based on the idea that creating reusable software components can save time and effort in the long run, by reducing duplication and ensuring that code is written once and used multiple times.

In practice, the CRP can be applied in several ways, including:

Creating reusable libraries or frameworks that provide a set of common functionality that can be used across multiple applications.
Designing classes and modules with a clear and well-defined purpose, and ensuring that they can be easily reused in different contexts.
Encouraging the use of design patterns and other best practices for creating reusable software components.
By applying the CRP, software designers can create software systems that are easier to maintain, modify, and extend over time, and that can provide a higher level of quality and consistency across different applications. However, it is important to balance the benefits of reusability with the costs and effort required to create and maintain reusable software components.

## Acyclic Dependencies Principle

The Acyclic Dependencies Principle (ADP) is a software design principle that states that dependencies between packages or modules in a software system should be acyclic. In other words, there should be no circular dependencies between packages or modules.

Circular dependencies can lead to several problems, including difficulty in understanding and modifying the system, increased risk of introducing bugs or unintended side effects, and reduced ability to reuse or test components in isolation.

To apply the ADP, software designers should strive to:

Identify and eliminate circular dependencies between packages or modules in the system.
Design packages or modules with well-defined and narrow responsibilities, so that they can be easily understood, reused, and tested in isolation.
Use techniques such as dependency injection or inversion of control to minimize the impact of dependencies between modules.
By applying the ADP, software designers can create software systems that are more modular, flexible, and maintainable over time, and that can be easily extended or adapted to meet changing requirements or use cases.

## Stable Dependcies Principle

The Stable Dependencies Principle (SDP) is a software design principle that states that packages or modules should depend on other packages or modules that are more stable than they are. Stability is measured by the degree of change that a package or module undergoes over time. A more stable module is one that is less likely to change, while a less stable module is one that is more likely to change.

According to the SDP, packages or modules that are more stable should be designed to have fewer dependencies, while packages or modules that are less stable should be designed to have more dependencies. This helps to ensure that changes to less stable packages or modules are less likely to affect more stable packages or modules, and that the system as a whole is more resilient to change.

In practice, the SDP can be applied in several ways, including:

Designing packages or modules with well-defined and narrow responsibilities, so that they are less likely to change over time.
Identifying and tracking changes to packages or modules over time, and using this information to inform design decisions and dependencies between modules.
Encouraging the use of design patterns and other best practices for reducing coupling and increasing cohesion between modules.
By applying the SDP, software designers can create software systems that are more resilient to change, and that can be easily maintained and extended over time.

# Software Design Patterns

Design patterns are general, reusable solutions to common problems in software design. They provide proven approaches to creating flexible, maintainable, and reusable software. Design patterns are organized into categories, including creational patterns, structural patterns, and behavioral patterns. By following design patterns, developers can save time and effort, improve communication and collaboration, and avoid common mistakes in software design.

## Creational Design Patterns

Creational design patterns are concerned with object creation mechanisms, trying to create objects in a manner suitable to the situation. They aim to abstract the object instantiation process while making the system more flexible and decoupled from the creation process.

The primary goal of Creational patterns is to make the system independent of how its objects are created, composed, and represented. They provide mechanisms to create objects in a manner suitable for a specific situation while ensuring that the creation is abstracted and decoupled from the system.

### Singleton Pattern

This pattern ensures that only one instance of a class is created and provides a global point of access to it. It is often used in situations where it is necessary to limit the number of instances of a class.

```cpp
class Singleton {
private:
    static Singleton* instance;
    Singleton() {}
public:
    static Singleton* getInstance() {
        if (instance == nullptr) {
            instance = new Singleton();
        }
        return instance;
    }
};

Singleton* Singleton::instance = nullptr;

int main() {
    Singleton* s1 = Singleton::getInstance();
    Singleton* s2 = Singleton::getInstance();
    assert(s1 == s2);
}
```

### Factory Pattern

This pattern provides an interface for creating objects, but allows subclasses to decide which class to instantiate. It is often used when there are multiple classes that can be instantiated from a single interface.

```cpp
class Animal {
public:
    virtual void makeSound() = 0;
};

class Dog : public Animal {
public:
    void makeSound() override {
        std::cout << "Woof!\n";
    }
};

class Cat : public Animal {
public:
    void makeSound() override {
        std::cout << "Meow!\n";
    }
};

class AnimalFactory {
public:
    virtual Animal* createAnimal() = 0;
};

class DogFactory : public AnimalFactory {
public:
    Animal* createAnimal() override {
        return new Dog();
    }
};

class CatFactory : public AnimalFactory {
public:
    Animal* createAnimal() override {
        return new Cat();
    }
};

int main() {
    AnimalFactory* dogFactory = new DogFactory();
    Animal* dog = dogFactory->createAnimal();
    dog->makeSound();

    AnimalFactory* catFactory = new CatFactory();
    Animal* cat = catFactory->createAnimal();
    cat->makeSound();
}

```

### Abstract Factory Pattern

This pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes. It is often used when there are multiple families of related objects that need to be created.

```cpp
// Abstract Product A interface
class Character {
public:
    virtual void attack() = 0;
};

// Concrete Product A1
class Warrior : public Character {
public:
    void attack() {
        std::cout << "Warrior attacks with a sword" << std::endl;
    }
};

// Concrete Product A2
class Mage : public Character {
public:
    void attack() {
        std::cout << "Mage attacks with a spell" << std::endl;
    }
};

// Abstract Product B interface
class Weapon {
public:
    virtual void use() = 0;
};

// Concrete Product B1
class Sword : public Weapon {
public:
    void use() {
        std::cout << "Warrior uses a sword" << std::endl;
    }
};

// Concrete Product B2
class Spell : public Weapon {
public:
    void use() {
        std::cout << "Mage uses a spell" << std::endl;
    }
};

// Abstract Factory interface
class AbstractFactory {
public:
    virtual Character* createCharacter() = 0;
    virtual Weapon* createWeapon() = 0;
};

// Concrete Factory 1
class WarriorFactory : public AbstractFactory {
public:
    Character* createCharacter() {
        return new Warrior();
    }

    Weapon* createWeapon() {
        return new Sword();
    }
};

// Concrete Factory 2
class MageFactory : public AbstractFactory {
public:
    Character* createCharacter() {
        return new Mage();
    }

    Weapon* createWeapon() {
        return new Spell();
    }
};

int main() {
    AbstractFactory* factory;
    Character* character;
    Weapon* weapon;

    // Create a Warrior and Sword using the WarriorFactory
    factory = new WarriorFactory();
    character = factory->createCharacter();
    weapon = factory->createWeapon();
    character->attack();
    weapon->use();

    // Create a Mage and Spell using the MageFactory
    factory = new MageFactory();
    character = factory->createCharacter();
    weapon = factory->createWeapon();
    character->attack();
    weapon->use();

    return 0;
}
```

### Builder Pattern

The Builder pattern is a creational design pattern that separates the construction of a complex object from its representation. It allows you to create different variations of the object by using the same construction process. Here's an example of how you can implement the Builder pattern in C++:

```cpp
#include <iostream>
#include <string>

// Product class
class Burger {
public:
    void setBun(const std::string& bun) {
        m_bun = bun;
    }

    void setPatty(const std::string& patty) {
        m_patty = patty;
    }

    void addTopping(const std::string& topping) {
        m_toppings += " " + topping;
    }

    void describe() const {
        std::cout << "Burger with " << m_bun << " bun, " << m_patty << " patty, and the following toppings:" << m_toppings << std::endl;
    }

private:
    std::string m_bun;
    std::string m_patty;
    std::string m_toppings;
};

// Abstract Builder interface
class BurgerBuilder {
public:
    virtual ~BurgerBuilder() {}

    virtual void buildBun() = 0;
    virtual void buildPatty() = 0;
    virtual void buildToppings() = 0;
    virtual Burger* getBurger() = 0;
};

// Concrete Builder 1
class CheeseburgerBuilder : public BurgerBuilder {
public:
    void buildBun() {
        m_burger->setBun("sesame seed");
    }

    void buildPatty() {
        m_burger->setPatty("beef");
    }

    void buildToppings() {
        m_burger->addTopping("cheese");
        m_burger->addTopping("lettuce");
        m_burger->addTopping("tomato");
    }

    Burger* getBurger() {
        return m_burger;
    }

private:
    Burger* m_burger = new Burger();
};

// Concrete Builder 2
class VeggieBurgerBuilder : public BurgerBuilder {
public:
    void buildBun() {
        m_burger->setBun("whole wheat");
    }

    void buildPatty() {
        m_burger->setPatty("veggie");
    }

    void buildToppings() {
        m_burger->addTopping("lettuce");
        m_burger->addTopping("tomato");
        m_burger->addTopping("avocado");
    }

    Burger* getBurger() {
        return m_burger;
    }

private:
    Burger* m_burger = new Burger();
};

// Director class
class BurgerDirector {
public:
    BurgerDirector(BurgerBuilder* builder)
        : m_builder(builder) {
    }

    void makeBurger() {
        m_builder->buildBun();
        m_builder->buildPatty();
        m_builder->buildToppings();
    }

    Burger* getBurger() {
        return m_builder->getBurger();
    }

private:
    BurgerBuilder* m_builder;
};

int main() {
    BurgerBuilder* builder = new CheeseburgerBuilder();
    BurgerDirector director(builder);
    director.makeBurger();
    Burger* burger = director.getBurger();
    burger->describe();

    builder = new VeggieBurgerBuilder();
    director = BurgerDirector(builder);
    director.makeBurger();
    burger = director.getBurger();
    burger->describe();

    return 0;
}
```

### Prototype Pattern

The Prototype pattern is a creational pattern that allows creating new objects by copying existing objects, rather than creating them from scratch. In this pattern, a client creates a prototype object, and then creates new objects by cloning the prototype.

```cpp
class Maze {
public:
    virtual Maze* Clone() const = 0;
    virtual void Print() const = 0;
};
class SmallMaze : public Maze {
public:
    Maze* Clone() const {
        return new SmallMaze(*this);
    }

    void Print() const {
        std::cout << "Small maze" << std::endl;
        // ... implementation for printing small maze ...
    }
};
class LargeMaze : public Maze {
public:
    Maze* Clone() const {
        return new LargeMaze(*this);
    }

    void Print() const {
        std::cout << "Large maze" << std::endl;
        // ... implementation for printing large maze ...
    }
};
int main() {
    Maze* smallMaze = new SmallMaze();
    Maze* largeMaze = new LargeMaze();

    Maze* clonedSmallMaze = smallMaze->Clone();
    Maze* clonedLargeMaze = largeMaze->Clone();

    smallMaze->Print();
    clonedSmallMaze->Print();

    largeMaze->Print();
    clonedLargeMaze->Print();

    delete smallMaze;
    delete largeMaze;
    delete clonedSmallMaze;
    delete clonedLargeMaze;

    return 0;
}
```

### Object Pool Pattern

The Object Pool pattern is a creational pattern that uses a pool of reusable objects instead of creating new objects every time they are needed. This can help reduce the overhead of creating new objects and improve performance.

Here's an example implementation of the Object Pool pattern in C++:

```cpp
#include <iostream>
#include <vector>

// The object to be reused (database connection)
class DatabaseConnection {
public:
    DatabaseConnection(const std::string& connectionString) :
        m_connectionString(connectionString),
        m_isOpen(false) {}

    bool Open() {
        if (!m_isOpen) {
            std::cout << "Opening database connection: " << m_connectionString << std::endl;
            m_isOpen = true;
        }
        return m_isOpen;
    }

    bool Close() {
        if (m_isOpen) {
            std::cout << "Closing database connection: " << m_connectionString << std::endl;
            m_isOpen = false;
        }
        return !m_isOpen;
    }

private:
    std::string m_connectionString;
    bool m_isOpen;
};

// The object pool
class ConnectionPool {
private:
    std::vector<DatabaseConnection*> m_connections;
    int m_maxSize;
    std::string m_connectionString;

public:
    ConnectionPool(const std::string& connectionString, int maxSize) :
        m_maxSize(maxSize),
        m_connectionString(connectionString) {
        // Populate the object pool with initial connections
        for (int i = 0; i < maxSize; i++) {
            m_connections.push_back(new DatabaseConnection(connectionString));
        }
    }

    DatabaseConnection* AcquireConnection() {
        DatabaseConnection* connection = nullptr;

        // Check if there is an available connection in the pool
        if (m_connections.size() > 0) {
            // Acquire a connection from the pool
            connection = m_connections.back();
            m_connections.pop_back();
        }
        else {
            // Create a new connection if the pool is empty
            connection = new DatabaseConnection(m_connectionString);
        }

        return connection;
    }

    void ReleaseConnection(DatabaseConnection* connection) {
        // Check if the pool is already full
        if (m_connections.size() >= m_maxSize) {
            // If the pool is full, delete the connection
            delete connection;
        }
        else {
            // Release the connection back to the pool
            connection->Close();
            m_connections.push_back(connection);
        }
    }
};

int main() {
    // Create a connection pool with a maximum of 3 connections
    ConnectionPool pool("localhost:3306", 3);

    // Acquire and release 5 connections
    for (int i = 0; i < 5; i++) {
        DatabaseConnection* connection = pool.AcquireConnection();
        connection->Open();
        // Do some database work...
        pool.ReleaseConnection(connection);
    }

    return 0;
}
```

## Structural Design Patterns

Structural design patterns are concerned with how objects and classes are composed to form larger structures or systems. These patterns provide ways to simplify the relationships between objects and classes, making it easier to modify, extend, and reuse code.

### Adapter Pattern

The Adapter pattern is a structural design pattern that allows objects with incompatible interfaces to collaborate by creating an adapter object that acts as a bridge between them. It is used when an existing class doesn't meet the requirements of a new system, and you want to reuse the class without modifying its code.

In the Adapter pattern, the adapter acts as an intermediary between the client and the adaptee. The client communicates with the adapter using a target interface, which the adapter then translates into the interface of the adaptee.

Here is an example in C++:

```cpp
#include <iostream>
#include <string>

// Target interface
class IVideoPlayer {
public:
    virtual void playAVI(std::string filename) = 0;
};

// Adaptee class
class MP4Player {
public:
    void playMP4(std::string filename) {
        std::cout << "Playing MP4 file: " << filename << std::endl;
    }
};

// Adapter class
class MP4PlayerAdapter : public IVideoPlayer {
private:
    MP4Player* mp4Player;

public:
    MP4PlayerAdapter(MP4Player* player) {
        mp4Player = player;
    }

    void playAVI(std::string filename) override {
        // Convert the AVI filename to MP4 filename
        std::string mp4Filename = filename.substr(0, filename.find_last_of(".")) + ".mp4";
        mp4Player->playMP4(mp4Filename);
    }
};

// Client code
void playVideo(IVideoPlayer* player, std::string filename) {
    player->playAVI(filename);
}

int main() {
    // Create an instance of the adaptee class
    MP4Player* mp4Player = new MP4Player();

    // Create an adapter object that wraps the adaptee
    IVideoPlayer* adapter = new MP4PlayerAdapter(mp4Player);

    // Play the video using the adapter object
    playVideo(adapter, "example.avi");

    delete mp4Player;
    delete adapter;

    return 0;
}
```

### Bridge Pattern

The Bridge pattern is a design pattern that allows you to separate the implementation of a feature from its abstraction, so that they can vary independently.

```cpp
#include <iostream>
using namespace std;

// Implementor interface
class TV {
public:
    virtual void on() = 0;
    virtual void off() = 0;
    virtual void setChannel(int channel) = 0;
    virtual void setVolume(int volume) = 0;
};

// Concrete Implementor 1
class SonyTV : public TV {
public:
    void on() {
        cout << "Sony TV is on" << endl;
    }
    void off() {
        cout << "Sony TV is off" << endl;
    }
    void setChannel(int channel) {
        cout << "Sony TV channel is set to " << channel << endl;
    }
    void setVolume(int volume) {
        cout << "Sony TV volume is set to " << volume << endl;
    }
};

// Concrete Implementor 2
class SamsungTV : public TV {
public:
    void on() {
        cout << "Samsung TV is on" << endl;
    }
    void off() {
        cout << "Samsung TV is off" << endl;
    }
    void setChannel(int channel) {
        cout << "Samsung TV channel is set to " << channel << endl;
    }
    void setVolume(int volume) {
        cout << "Samsung TV volume is set to " << volume << endl;
    }
};

// Abstraction interface
class RemoteControl {
public:
    virtual void turnOn() = 0;
    virtual void turnOff() = 0;
    virtual void setChannel(int channel) = 0;
    virtual void setVolume(int volume) = 0;
    virtual void show() = 0;

protected:
    TV* tv;
};

// Refined Abstraction 1
class BasicRemoteControl : public RemoteControl {
public:
    BasicRemoteControl(TV* tv) {
        this->tv = tv;
    }
    void turnOn() {
        tv->on();
    }
    void turnOff() {
        tv->off();
    }
    void setChannel(int channel) {
        tv->setChannel(channel);
    }
    void setVolume(int volume) {
        tv->setVolume(volume);
    }
    void show() {
        cout << "Basic Remote Control:" << endl;
    }
};

// Refined Abstraction 2
class AdvancedRemoteControl : public RemoteControl {
public:
    AdvancedRemoteControl(TV* tv) {
        this->tv = tv;
    }
    void turnOn() {
        tv->on();
    }
    void turnOff() {
        tv->off();
    }
    void setChannel(int channel) {
        tv->setChannel(channel);
    }
    void setVolume(int volume) {
        tv->setVolume(volume);
    }
    void mute() {
        tv->setVolume(0);
        cout << "TV is muted" << endl;
    }
    void show() {
        cout << "Advanced Remote Control:" << endl;
    }
};

// Client code
int main() {
    TV* sony = new SonyTV();
    TV* samsung = new SamsungTV();

    RemoteControl* basicRemote = new BasicRemoteControl(sony);
    RemoteControl* advancedRemote = new AdvancedRemoteControl(samsung);

    basicRemote->show();
    basicRemote->turnOn();
    basicRemote->setChannel(3);
    basicRemote->setVolume(10);
    basicRemote->turnOff();

    advancedRemote->show();
    advancedRemote->turnOn();
    advancedRemote->setChannel(7);
    advancedRemote->setVolume(20);
    advancedRemote->mute();
    advancedRemote->turnOff();

}
```

### Composite Pattern

The Composite pattern is a structural design pattern that allows you to treat a group of objects in the same way as a single object. It composes objects into tree structures to represent part-whole hierarchies.

In the Composite pattern, there are two types of objects: the composite object and the leaf object. The composite object represents a group of objects and contains a list of its child objects, while the leaf object represents an individual object in the group.

Here's an example implementation of the Composite pattern in C++:

```cpp
#include <iostream>
#include <vector>

class FileSystemNode {
public:
    virtual std::string getName() = 0;
    virtual void ls() = 0;
    virtual void addNode(FileSystemNode* node) {}
    virtual void removeNode(FileSystemNode* node) {}
};

class File : public FileSystemNode {
public:
    File(std::string name) : name(name) {}

    std::string getName() {
        return name;
    }

    void ls() {
        std::cout << getName() << std::endl;
    }

private:
    std::string name;
};

class Directory : public FileSystemNode {
public:
    Directory(std::string name) : name(name) {}

    std::string getName() {
        return name;
    }

    void ls() {
        std::cout << getName() << "/" << std::endl;
        for (FileSystemNode* node : nodes) {
            std::cout << "  ";
            node->ls();
        }
    }

    void addNode(FileSystemNode* node) {
        nodes.push_back(node);
    }

    void removeNode(FileSystemNode* node) {
        nodes.erase(std::remove(nodes.begin(), nodes.end(), node), nodes.end());
    }

private:
    std::string name;
    std::vector<FileSystemNode*> nodes;
};

int main() {
    FileSystemNode* file1 = new File("file1.txt");
    FileSystemNode* file2 = new File("file2.txt");

    FileSystemNode* dir1 = new Directory("dir1");
    dir1->addNode(file1);

    FileSystemNode* dir2 = new Directory("dir2");
    dir2->addNode(file2);

    FileSystemNode* root = new Directory("root");
    root->addNode(dir1);
    root->addNode(dir2);

    root->ls();

    return 0;
}
```

### Decorator Pattern

The Decorator pattern is used to dynamically add functionality to an object by wrapping it in a decorator class. The decorator class has the same interface as the original object, and adds its own behavior before or after calling the original object's methods.

```cpp
class Pizza {
public:
    virtual ~Pizza() {}
    virtual int get_cost() = 0;
};

class Margherita : public Pizza {
public:
    int get_cost() override {
        return 10;
    }
};

class Pepperoni : public Pizza {
public:
    int get_cost() override {
        return 12;
    }
};

class PizzaDecorator : public Pizza {
public:
    PizzaDecorator(Pizza* pizza) : pizza_(pizza) {}
protected:
    Pizza* pizza_;
};

class Cheese : public PizzaDecorator {
public:
    Cheese(Pizza* pizza) : PizzaDecorator(pizza) {}
    int get_cost() override {
        return pizza_->get_cost() + 2;
    }
};

class Ham : public PizzaDecorator {
public:
    Ham(Pizza* pizza) : PizzaDecorator(pizza) {}
    int get_cost() override {
        return pizza_->get_cost() + 3;
    }
};

int main(){
    Pizza* margherita = new Margherita();
    Pizza* margherita_with_cheese = new Cheese(margherita);
    Pizza* pepperoni_with_cheese_and_ham = new Ham(new Cheese(new Pepperoni()));

    std::cout << margherita_with_cheese->get_cost() << std::endl;  // output: 12
    std::cout << pepperoni_with_cheese_and_ham->get_cost() << std::endl;  // output: 17

    return 0;
}
```

### Facade Pattern

The Facade pattern is a structural design pattern that provides a simplified interface to a complex system or group of subsystems. It provides a high-level interface that makes the subsystem easier to use and reduces the complexity of the code.

```cpp
#include <iostream>
#include <string>

class EmailService {
public:
    void sendEmail(std::string email, std::string message) {
        std::cout << "Sending email to " << email << ": " << message << std::endl;
    }
};

class SMSService {
public:
    void sendSMS(std::string phone, std::string message) {
        std::cout << "Sending SMS to " << phone << ": " << message << std::endl;
    }
};

class PushNotificationService {
public:
    void sendPushNotification(std::string deviceToken, std::string message) {
        std::cout << "Sending push notification to " << deviceToken << ": " << message << std::endl;
    }
};

class NotificationSystem {
private:
    EmailService emailService;
    SMSService smsService;
    PushNotificationService pushNotificationService;
public:
    void sendNotification(std::string email, std::string phone, std::string deviceToken, std::string message) {
        emailService.sendEmail(email, message);
        smsService.sendSMS(phone, message);
        pushNotificationService.sendPushNotification(deviceToken, message);
    }
};

int main() {
    NotificationSystem notificationSystem;
    notificationSystem.sendNotification("johndoe@example.com", "+1234567890", "abcd1234", "Hello, world!");
    return 0;
}
```

### Flyweight Pattern

The Flyweight design pattern is a structural pattern that helps to minimize the memory usage of an application by sharing objects that have similar data.

```cpp
 #include <iostream>
#include <string>
#include <unordered_map>

using namespace std;

// The Flyweight class
class Character {
public:
    virtual void render() = 0;
};

// The ConcreteFlyweight class
class Player : public Character {
public:
    Player(string name, int health, int attackPower, string image) {
        this->name = name;
        this->health = health;
        this->attackPower = attackPower;
        this->image = image;
    }

    void render() {
        cout << "Name: " << name << endl;
        cout << "Health: " << health << endl;
        cout << "Attack Power: " << attackPower << endl;
        cout << "Image: " << image << endl;
        cout << endl;
    }

private:
    string name;
    int health;
    int attackPower;
    string image;
};

// The FlyweightFactory class
class CharacterFactory {
public:
    Character* getCharacter(string name) {
        if (characters.find(name) == characters.end()) {
            // If character does not exist, create a new one and add it to the pool
            cout << "Creating new character: " << name << endl;
            characters[name] = new Player(name, 100, 10, "player.png");
        }
        else {
            // If character exists, return the existing one from the pool
            cout << "Returning existing character: " << name << endl;
        }
        return characters[name];
    }

    ~CharacterFactory() {
        for (auto it : characters) {
            delete it.second;
        }
        characters.clear();
    }

private:
    unordered_map<string, Character*> characters;
};

int main() {
    CharacterFactory* factory = new CharacterFactory();

    // Get two instances of the same character
    Character* player1 = factory->getCharacter("Player1");
    Character* player2 = factory->getCharacter("Player1");

    // Get a new instance of a different character
    Character* player3 = factory->getCharacter("Player2");

    // Render the characters
    player1->render();
    player2->render();
    player3->render();

    // Clean up memory
    delete factory;

    return 0;
}
```

### Proxy Pattern

The Proxy pattern is a structural pattern that provides a surrogate or placeholder object to control access to another object. The proxy object acts as an intermediary between the client and the real object, and it can perform additional tasks such as caching, security checks, or resource management.

```cpp
#include <iostream>
#include <string>

using namespace std;

// The Subject interface
class BankAccount {
public:
    virtual void deposit(int amount) = 0;
    virtual void withdraw(int amount) = 0;
    virtual int getBalance() = 0;
};

// The RealSubject class
class RealBankAccount : public BankAccount {
public:
    RealBankAccount(string name, string password) {
        this->name = name;
        this->password = password;
        balance = 0;
    }

    void deposit(int amount) {
        balance += amount;
        cout << "Deposit successful. New balance: " << balance << endl;
    }

    void withdraw(int amount) {
        if (balance >= amount) {
            balance -= amount;
            cout << "Withdrawal successful. New balance: " << balance << endl;
        }
        else {
            cout << "Insufficient funds." << endl;
        }
    }

    int getBalance() {
        return balance;
    }

private:
    string name;
    string password;
    int balance;
};

// The Proxy class
class BankAccountProxy : public BankAccount {
public:
    BankAccountProxy(string name, string password) {
        this->name = name;
        this->password = password;
        account = nullptr;
    }

    void deposit(int amount) {
        if (authorize()) {
            if (account == nullptr) {
                account = new RealBankAccount(name, password);
            }
            account->deposit(amount);
        }
    }

    void withdraw(int amount) {
        if (authorize()) {
            if (account == nullptr) {
                account = new RealBankAccount(name, password);
            }
            account->withdraw(amount);
        }
    }

    int getBalance() {
        if (authorize()) {
            if (account == nullptr) {
                account = new RealBankAccount(name, password);
            }
            return account->getBalance();
        }
        else {
            return -1;
        }
    }

private:
    bool authorize() {
        // Authenticate the user based on name and password
        // Check if the user has the required permissions
        return true;
    }

    string name;
    string password;
    RealBankAccount* account;
};

int main() {
    BankAccount* account = new BankAccountProxy("Alice", "password");

    account->deposit(100);
    account->withdraw(50);
    cout << "Balance: " << account->getBalance() << endl;

    delete account;

    return 0;
}
```

## Behavioral Design Patterns

Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects. They deal with communication between objects, encapsulating behaviors in objects, and controlling the flow of communication. The key objective of these patterns is to improve communication between objects to make the system more flexible and efficient.

### Chain of Responsiblity Pattern

The Chain of Responsibility pattern is a behavioral design pattern that allows an object to pass a request through a chain of handlers until it is handled by an appropriate handler. This pattern is useful when multiple objects may be able to handle a request, and the client does not know which object will be able to handle the request.

```cpp
#include <iostream>
#include <string>
using namespace std;

// Abstract base class for handlers
class OrderHandler {
public:
    virtual void setNext(OrderHandler* nextHandler) = 0;
    virtual void handleOrder(string vendor, string item, int quantity, string address) = 0;
};

// Concrete handler that checks if the item is in stock
class InventoryHandler : public OrderHandler {
private:
    OrderHandler* nextHandler;
public:
    void setNext(OrderHandler* nextHandler) {
        this->nextHandler = nextHandler;
    }

    void handleOrder(string vendor, string item, int quantity, string address) {
        // Check if the item is in stock for the given vendor
        bool isInStock = checkInventory(vendor, item, quantity);

        if (isInStock) {
            // If the item is in stock, pass the order to the next handler
            nextHandler->handleOrder(vendor, item, quantity, address);
        } else {
            cout << "Sorry, item is out of stock" << endl;
        }
    }

    bool checkInventory(string vendor, string item, int quantity) {
        // Check inventory for the given vendor and item
        // Return true if there is enough inventory to fulfill the order
        // Return false if there is not enough inventory to fulfill the order
        return true;
    }
};

// Concrete handler that checks the shipping address
class AddressHandler : public OrderHandler {
private:
    OrderHandler* nextHandler;
public:
    void setNext(OrderHandler* nextHandler) {
        this->nextHandler = nextHandler;
    }

    void handleOrder(string vendor, string item, int quantity, string address) {
        // Check if the shipping address is valid
        bool isAddressValid = checkAddress(address);

        if (isAddressValid) {
            // If the address is valid, pass the order to the next handler
            nextHandler->handleOrder(vendor, item, quantity, address);
        } else {
            cout << "Sorry, invalid shipping address" << endl;
        }
    }

    bool checkAddress(string address) {
        // Check if the address is valid
        // Return true if the address is valid
        // Return false if the address is invalid
        return true;
    }
};

// Concrete handler that processes the payment
class PaymentHandler : public OrderHandler {
private:
    OrderHandler* nextHandler;
public:
    void setNext(OrderHandler* nextHandler) {
        this->nextHandler = nextHandler;
    }

    void handleOrder(string vendor, string item, int quantity, string address) {
        // Process the payment for the order
        bool isPaymentProcessed = processPayment();

        if (isPaymentProcessed) {
            cout << "Order for " << quantity << " " << item << " from " << vendor << " to " << address << " processed successfully" << endl;
        } else {
            cout << "Sorry, payment processing failed" << endl;
        }
    }

    bool processPayment() {
        // Process the payment for the order
        // Return true if the payment is processed successfully
        // Return false if the payment processing fails
        return true;
    }
};

int main() {
    // Create the chain of handlers
    OrderHandler* inventoryHandler = new InventoryHandler();
    OrderHandler* addressHandler = new AddressHandler();
    OrderHandler* paymentHandler = new PaymentHandler();

    inventoryHandler->setNext(addressHandler);
    addressHandler->setNext(paymentHandler);

    // Process an order
    inventoryHandler->handleOrder("Acme", "Widget", 10, "123 Main St.");

    return 0;
}
```

### Command Pattern

The Command pattern is a behavioral design pattern that allows you to encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations. In simpler terms, it provides a way to separate the request for an action from the object that actually performs the action.

The pattern consists of several components: the Command, which is an object that contains information about an action to be performed; the Receiver, which is an object that performs the action; the Invoker, which is an object that receives the Command and asks the Receiver to perform the action; and the Client, which creates the Command and sends it to the Invoker.

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

// The abstract command class
class Command {
public:
    virtual void execute() = 0;
    virtual void undo() = 0;
};

// A concrete command for inserting text
class InsertCommand : public Command {
private:
    string text;
    int position;
    string previousText;
public:
    InsertCommand(string text, int position) {
        this->text = text;
        this->position = position;
    }

    void execute() {
        // Save the previous text at the insertion position
        previousText = document.substr(position, text.length());

        // Insert the new text at the insertion position
        document.replace(position, text.length(), text);
    }

    void undo() {
        // Restore the previous text at the insertion position
        document.replace(position, text.length(), previousText);
    }
};

// A concrete command for deleting text
class DeleteCommand : public Command {
private:
    int position;
    string deletedText;
public:
    DeleteCommand(int position, int length) {
        this->position = position;
        deletedText = document.substr(position, length);
    }

    void execute() {
        // Delete the text at the deletion position
        document.erase(position, deletedText.length());
    }

    void undo() {
        // Insert the deleted text at the deletion position
        document.insert(position, deletedText);
    }
};

// The invoker
class TextEditor {
private:
    vector<Command*> undoStack;
public:
    void executeCommand(Command* command) {
        command->execute();
        undoStack.push_back(command);
    }

    void undoLastCommand() {
        if (!undoStack.empty()) {
            Command* lastCommand = undoStack.back();
            lastCommand->undo();
            undoStack.pop_back();
        }
    }
};

// The client code
int main() {
    TextEditor textEditor;

    // Insert some text
    Command* insertCommand = new InsertCommand("Hello, world!", 0);
    textEditor.executeCommand(insertCommand);

    // Delete some text
    Command* deleteCommand = new DeleteCommand(5, 7);
    textEditor.executeCommand(deleteCommand);

    // Undo the last command
    textEditor.undoLastCommand();

    // Print the document
    cout << document << endl;

    return 0;
}
```

### Observer Pattern

The observer pattern is used to maintain a one-to-many relationship between objects so that when one object changes state, all its dependents are notified and updated automatically. This pattern is often used to implement event handling, where multiple objects need to react to a change in state.

```cpp
#include <iostream>
#include <vector>
using namespace std;

// The abstract Observer class
class Observer {
public:
    virtual void update(int temperature) = 0;
};

// The concrete Subject class
class TemperatureSensor {
private:
    vector<Observer*> observers;
    int temperature;
public:
    void addObserver(Observer* observer) {
        observers.push_back(observer);
    }

    void removeObserver(Observer* observer) {
        for (int i = 0; i < observers.size(); i++) {
            if (observers[i] == observer) {
                observers.erase(observers.begin() + i);
                break;
            }
        }
    }

    void setTemperature(int temperature) {
        this->temperature = temperature;
        notifyObservers();
    }

    int getTemperature() {
        return temperature;
    }

    void notifyObservers() {
        for (int i = 0; i < observers.size(); i++) {
            observers[i]->update(temperature);
        }
    }
};

// A concrete Observer that prints the temperature to the console
class ConsoleDisplay : public Observer {
public:
    void update(int temperature) {
        cout << "Temperature: " << temperature << endl;
    }
};

// A concrete Observer that sends an alert if the temperature goes above a certain threshold
class AlertSystem : public Observer {
private:
    int threshold;
public:
    AlertSystem(int threshold) {
        this->threshold = threshold;
    }

    void update(int temperature) {
        if (temperature > threshold) {
            cout << "ALERT: Temperature is above threshold!" << endl;
        }
    }
};

// The client code
int main() {
    TemperatureSensor temperatureSensor;
    ConsoleDisplay consoleDisplay;
    AlertSystem alertSystem(30);

    temperatureSensor.addObserver(&consoleDisplay);
    temperatureSensor.addObserver(&alertSystem);

    temperatureSensor.setTemperature(25);
    temperatureSensor.setTemperature(30);
    temperatureSensor.setTemperature(35);

    temperatureSensor.removeObserver(&alertSystem);

    temperatureSensor.setTemperature(40);

    return 0;
}
```

### Iterator Pattern

The iterator pattern is used to provide a way to access the elements of a collection object in a sequential manner, without exposing its underlying representation. The iterator pattern decouples the algorithm that iterates over the collection from the collection itself, making the algorithm more generic and reusable.

```cpp
#include <iostream>
#include <vector>
using namespace std;

// The abstract Iterator class
class Iterator {
public:
    virtual bool hasNext() = 0;
    virtual void* next() = 0;
};

// The concrete Iterator class for iterating over books
class BookIterator : public Iterator {
private:
    vector<string> books;
    int position = 0;
public:
    BookIterator(vector<string> books) {
        this->books = books;
    }

    bool hasNext() {
        return position < books.size();
    }

    void* next() {
        if (hasNext()) {
            string& book = books[position++];
            return &book;
        }
        return nullptr;
    }
};

// The aggregate class that holds the collection of books
class Library {
private:
    vector<string> books;
public:
    void addBook(string book) {
        books.push_back(book);
    }

    Iterator* createIterator() {
        return new BookIterator(books);
    }
};

// The client code
int main() {
    Library library;
    library.addBook("The Great Gatsby");
    library.addBook("To Kill a Mockingbird");
    library.addBook("Pride and Prejudice");

    Iterator* bookIterator = library.createIterator();
    while (bookIterator->hasNext()) {
        string* book = static_cast<string*>(bookIterator->next());
        cout << *book << endl;
    }

    delete bookIterator;

    return 0;
}
```

### State Pattern

The state pattern is a behavioral pattern used in software design to allow an object to alter its behavior when its internal state changes. The pattern involves defining a set of states that an object can be in, and specifying the behavior of the object for each state. The object's behavior is then determined by its current state.

```cpp
#include <iostream>
#include <string>
using namespace std;

// The abstract State class
class State {
public:
    virtual void addProduct(string product) = 0;
    virtual void removeProduct(string product) = 0;
    virtual void checkout() = 0;
};

// The concrete State class for an empty shopping cart
class EmptyCartState : public State {
public:
    void addProduct(string product) {
        cout << "Added product: " << product << endl;
    }

    void removeProduct(string product) {
        cout << "Cannot remove product, cart is empty" << endl;
    }

    void checkout() {
        cout << "Cannot checkout, cart is empty" << endl;
    }
};

// The concrete State class for a non-empty shopping cart
class NonEmptyCartState : public State {
public:
    void addProduct(string product) {
        cout << "Added product: " << product << endl;
    }

    void removeProduct(string product) {
        cout << "Removed product: " << product << endl;
    }

    void checkout() {
        cout << "Checked out" << endl;
    }
};

// The Context class that manages the current state of the shopping cart
class ShoppingCart {
private:
    State* state;
public:
    ShoppingCart() {
        state = new EmptyCartState();
    }

    void setState(State* state) {
        this->state = state;
    }

    void addProduct(string product) {
        state->addProduct(product);
        setState(new NonEmptyCartState());
    }

    void removeProduct(string product) {
        state->removeProduct(product);
        if (state == dynamic_cast<NonEmptyCartState*>(state)) {
            return;
        }
        setState(new EmptyCartState());
    }

    void checkout() {
        state->checkout();
        setState(new EmptyCartState());
    }
};

// The client code
int main() {
    ShoppingCart cart;

    cart.addProduct("T-shirt");
    cart.addProduct("Jeans");
    cart.checkout();

    cart.addProduct("Sneakers");
    cart.removeProduct("T-shirt");
    cart.removeProduct("Jeans");

    return 0;
}
```

### Visitor Pattern

The visitor pattern is a behavioral pattern used in software design to separate the algorithm for processing an object from the object itself. The pattern involves defining a visitor object that can visit and operate on a set of objects that implement a common interface.

```cpp
// Forward declaration of employee classes
class Manager;
class Engineer;
class Intern;

// Abstract visitor class
class Visitor {
public:
    virtual void visit(Manager* manager) = 0;
    virtual void visit(Engineer* engineer) = 0;
    virtual void visit(Intern* intern) = 0;
};

// Concrete employee classes
class Employee {
public:
    virtual void accept(Visitor* visitor) = 0;
};

class Manager : public Employee {
public:
    void accept(Visitor* visitor) override {
        visitor->visit(this);
    }
    int getSalary() const {
        return 5000;
    }
};

class Engineer : public Employee {
public:
    void accept(Visitor* visitor) override {
        visitor->visit(this);
    }
    int getSalary() const {
        return 3000;
    }
};

class Intern : public Employee {
public:
    void accept(Visitor* visitor) override {
        visitor->visit(this);
    }
    int getSalary() const {
        return 1000;
    }
};

// Concrete visitor class
class SalaryVisitor : public Visitor {
public:
    void visit(Manager* manager) override {
        totalSalary += manager->getSalary() * 2;
    }
    void visit(Engineer* engineer) override {
        totalSalary += engineer->getSalary();
    }
    void visit(Intern* intern) override {
        totalSalary += intern->getSalary() / 2;
    }
    int getTotalSalary() const {
        return totalSalary;
    }
private:
    int totalSalary = 0;
};

// Client code
int main() {
    std::vector<Employee*> employees {
        new Manager(),
        new Engineer(),
        new Intern(),
        new Manager(),
        new Engineer(),
    };
    SalaryVisitor visitor;
    for (auto employee : employees) {
        employee->accept(&visitor);
    }
    std::cout << "Total salary: " << visitor.getTotalSalary() << std::endl;
    for (auto employee : employees) {
        delete employee;
    }
    return 0;
}
```

### Mediator Pattern

The mediator pattern is a behavioral pattern used in software design to reduce the complexity of communication between objects by introducing a mediator object that encapsulates the communication logic. The mediator pattern promotes loose coupling between objects by eliminating the need for objects to communicate directly with each other.

```cpp
#include <iostream>
#include <string>
#include <vector>

// Forward declaration of user classes
class User;
class ChatMediator;

// Abstract mediator class
class ChatMediator {
public:
    virtual void send(const std::string& message, User* sender) = 0;
};

// Concrete user classes
class User {
public:
    User(const std::string& name, ChatMediator* mediator)
        : name(name), mediator(mediator) {}

    const std::string& getName() const {
        return name;
    }

    void send(const std::string& message) {
        mediator->send(message, this);
    }

    void receive(const std::string& message, User* sender) {
        std::cout << name << " received message from " << sender->getName() << ": " << message << std::endl;
    }

private:
    std::string name;
    ChatMediator* mediator;
};

// Concrete mediator class
class ChatRoom : public ChatMediator {
public:
    void addUser(User* user) {
        users.push_back(user);
    }

    void send(const std::string& message, User* sender) override {
        for (auto user : users) {
            if (user != sender) {
                user->receive(message, sender);
            }
        }
    }

private:
    std::vector<User*> users;
};

// Client code
int main() {
    ChatRoom chatRoom;
    User alice("Alice", &chatRoom);
    User bob("Bob", &chatRoom);
    User charlie("Charlie", &chatRoom);

    chatRoom.addUser(&alice);
    chatRoom.addUser(&bob);
    chatRoom.addUser(&charlie);

    alice.send("Hello everyone!");
    bob.send("Hey Alice!");
    charlie.send("Nice to meet you all!");

    return 0;
}
```

### Memento Pattern

The Memento pattern is a behavioral design pattern that allows an object to save and restore its internal state without violating encapsulation. This pattern is useful when you want to be able to undo changes made to an object's state or when you need to be able to restore an object's state to a previous state.
The pattern involves three main components:

Originator: This is the object whose state needs to be saved and restored. It creates a memento object that contains a snapshot of its state.

Memento: This is an object that stores the state of the originator. The memento object is typically read-only and can only be accessed by the originator.

Caretaker: This is an object that is responsible for keeping track of mementos. It can save mementos, retrieve mementos, and pass mementos back to the originator to restore its state.

```cpp
#include <iostream>
#include <string>
#include <vector>

// Memento class
class DocumentMemento {
public:
    DocumentMemento(const std::string& content) : content(content) {}
    const std::string& getContent() const { return content; }

private:
    std::string content;
};

// Originator class
class TextEditor {
public:
    void setContent(const std::string& content) {
        this->content = content;
        std::cout << "Content set to: " << content << std::endl;
    }

    DocumentMemento createMemento() const {
        return DocumentMemento(content);
    }

    void restoreMemento(const DocumentMemento& memento) {
        content = memento.getContent();
        std::cout << "Content restored to: " << content << std::endl;
    }

private:
    std::string content;
};

// Caretaker class
class History {
public:
    void addMemento(const DocumentMemento& memento) {
        mementos.push_back(memento);
    }

    DocumentMemento getMemento(int index) const {
        return mementos[index];
    }

    int getSize() const {
        return mementos.size();
    }

private:
    std::vector<DocumentMemento> mementos;
};

// Client code
int main() {
    TextEditor textEditor;
    History history;

    // Edit document and save mementos
    textEditor.setContent("First version of the document");
    history.addMemento(textEditor.createMemento());

    textEditor.setContent("Second version of the document");
    history.addMemento(textEditor.createMemento());

    textEditor.setContent("Third version of the document");
    history.addMemento(textEditor.createMemento());

    // Restore previous version of the document
    int index = 1; // Index of the memento to restore
    textEditor.restoreMemento(history.getMemento(index));

    return 0;
}
```

### Strategy Pattern

This pattern is used to define a family of algorithms, encapsulate each one, and make them interchangeable. The strategy pattern allows the algorithms to vary independently of the clients that use them, and it enables the selection of an algorithm at runtime based on specific needs.

```cpp
#include <iostream>

// Weapon base class
class Weapon {
public:
    virtual void useWeapon() = 0;
};

// Sword concrete class
class Sword : public Weapon {
public:
    void useWeapon() {
        std::cout << "Using a sword to attack!" << std::endl;
    }
};

// Bow concrete class
class Bow : public Weapon {
public:
    void useWeapon() {
        std::cout << "Using a bow to attack!" << std::endl;
    }
};

// Character class
class Character {
public:
    Character(Weapon* weapon) : weapon(weapon) {}

    void setWeapon(Weapon* weapon) {
        this->weapon = weapon;
    }

    void attack() {
        weapon->useWeapon();
    }

private:
    Weapon* weapon;
};

// Client code
int main() {
    // Create a character with a sword
    Sword sword;
    Character character(&sword);
    character.attack();

    // Switch the character's weapon to a bow
    Bow bow;
    character.setWeapon(&bow);
    character.attack();

    return 0;
}
```

### Template Metohd Pattern

The template method pattern is used to define the skeleton of an algorithm in a base class, with certain steps deferred to subclasses. This pattern allows subclasses to redefine certain steps of the algorithm without changing its overall structure.

```cpp
#include <iostream>

// Report base class
class Report {
public:
    // Template method
    void createReport() {
        createHeader();
        createBody();
        createFooter();
    }

    // Abstract methods
    virtual void createHeader() = 0;
    virtual void createBody() = 0;
    virtual void createFooter() = 0;
};

// PDF report class
class PdfReport : public Report {
public:
    // Override abstract methods to create PDF-specific content
    void createHeader() {
        std::cout << "Creating PDF header..." << std::endl;
    }

    void createBody() {
        std::cout << "Creating PDF body..." << std::endl;
    }

    void createFooter() {
        std::cout << "Creating PDF footer..." << std::endl;
    }
};

// CSV report class
class CsvReport : public Report {
public:
    // Override abstract methods to create CSV-specific content
    void createHeader() {
        std::cout << "Creating CSV header..." << std::endl;
    }

    void createBody() {
        std::cout << "Creating CSV body..." << std::endl;
    }

    void createFooter() {
        std::cout << "Creating CSV footer..." << std::endl;
    }
};

// Client code
int main() {
    // Create a PDF report and create it
    PdfReport pdfReport;
    pdfReport.createReport();

    // Create a CSV report and create it
    CsvReport csvReport;
    csvReport.createReport();

    return 0;
}
```

# Software Architectural Patterns

A software architectural pattern is a general, reusable solution to a commonly occurring problem in software architecture. It provides a template or a blueprint for how to organize and structure software systems to achieve a set of desired qualities, such as maintainability, scalability, flexibility, and modifiability.

## Client-Server Architectures

Client-server architecture is a common software architecture pattern where a client application communicates with a server over a network. In this pattern, the client is typically a user-facing application that runs on a desktop or mobile device, while the server is a backend system that provides services to the client.

## Model-view controller Architecture

Model-View-Controller (MVC) separates an application into three interconnected components: a model that represents the data and business logic, a view that displays the user interface, and a controller that handles user input and updates the model and view accordingly.

## Layered Architecture

Layered architecture: divides an application into multiple layers, each responsible for a specific set of functions. This helps to modularize the system, making it easier to manage and maintain.

## Enterprise Architecture

Enterprise architecture (EA) is a discipline that involves the planning, design, implementation, and management of an organization's information technology (IT) infrastructure and related resources to align with the organization's overall business goals and objectives.

Enterprise architecture takes a holistic view of the entire organization and its environment, including people, processes, information, technology, and other resources. It provides a framework for organizations to plan and manage their IT investments, ensure alignment between IT and business strategies, and enable effective decision-making.

## Business Architecture

Business architecture is a component of enterprise architecture that describes the organization's business processes, capabilities, goals, and strategies, and how they relate to the overall IT architecture. Business architecture provides a framework for understanding and managing the organization's operations, and how they contribute to achieving the organization's overall objectives.

## Information System Architecture

Information system architecture is the design and structure of an organization's information systems, including hardware, software, databases, networks, and other components. It provides a framework for organizing and integrating information and technology resources to meet the organization's objectives.

## Application Architecture & Data Architecture

Application architecture refers to the structure and design of the software applications used by an organization, including their components, interactions, and interfaces. Application architecture includes several key components, including:

1. User interface: defines the way users interact with the application, including the layout, design, and functionality of the application's interface.

2. Business logic: describes the rules and algorithms that govern the application's behavior and processing of data.

3. Data access: specifies how the application retrieves and manipulates data, including the data storage technologies used.

4. Integration: defines how the application interacts with other applications and systems, including the use of APIs, web services, and other integration technologies.

Data architecture, on the other hand, refers to the design and management of an organization's data resources, including how data is stored, processed, and managed. Data architecture includes several key components, including:
Data models: describes the structure and relationships between different types of data, including entities, attributes, and relationships.

1. Data models: describes the structure and relationships between different types of data, including entities, attributes, and relationships.

2. Data storage: defines the physical storage of data, including the use of databases, data warehouses, and other storage technologies.

3. Data integration: specifies how data from different sources is combined and transformed to provide a unified view of the organization's data.

4. Data security: describes the measures used to protect the organization's data from unauthorized access or theft.
