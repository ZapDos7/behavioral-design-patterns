# Introduction

A **design pattern** is a way of structuring code in order to solve a specific problem.

Pros:
 - common problems can have similar solutions
 - reuse existing knowledge
 - flexible, shorter, reusable, & more elegant code of better quality
 - having guidelines saves time

## History
[Design Patterns: Elements of Reusable Object-Oriented Software](http://www.javier8a.com/itc/bd1/articulo.pdf) (1994) by Erich Gamma, John Vlissides, Ralph Johnson, Richard Helm (*the gang of four*)

## Table of Contents
- [Java Design Patterns: Creational](#java-design-patterns--creational)
  * [What are creational design patterns?](#what-are-creational-design-patterns-)
  * [Pattern 1: The Builder Pattern](#pattern-1--the-builder-pattern)
    + [Exercise 1](#exercise-1)
  * [Pattern 2: The Singleton Pattern](#pattern-2--the-singleton-pattern)
    + [Exercise 2a](#exercise-2a)
    + [Exercise 2b](#exercise-2b)
    + [Exercise 2c](#exercise-2c)
  * [Pattern 3: The Prototype Pattern](#pattern-3--the-prototype-pattern)
    + [Exercise 3a](#exercise-3a)
    + [Exercise 3b](#exercise-3b)
  * [Pattern 4: The Factory Method Pattern](#pattern-4--the-factory-method-pattern)
    + [Exercise 4a](#exercise-4a)
    + [Exercise 4b](#exercise-4b)
    + [Exercise 4c](#exercise-4c)
  * [Pattern 5: The Abstract Factory Pattern](#pattern-5--the-abstract-factory-pattern)
    + [Exercise 5a](#exercise-5a)
    + [Exercise 5b](#exercise-5b)
    + [Exercise 5c](#exercise-5c)
- [Java Design Patterns: Behavioral Part 1](#java-design-patterns--behavioral-part-1)
  * [What are behavioral design patterns?](#what-are-behavioral-design-patterns-)
  * [Types of behavioral design patterns:](#types-of-behavioral-design-patterns-)
  * [Pattern 1: Chain of Responsibility](#pattern-1--chain-of-responsibility)
    + [Exercise 1](#exercise-1-1)
    + [Challenge 1](#challenge-1)
  * [Pattern 2: The Command Pattern](#pattern-2--the-command-pattern)
    + [Exercise 2](#exercise-2)
    + [Challenge 2](#challenge-2)
  * [Pattern 3: Interpreter Pattern](#pattern-3--interpreter-pattern)
    + [Exercise 3](#exercise-3)
    + [Challenge 3](#challenge-3)
  * [Pattern 4: Iterator Pattern](#pattern-4--iterator-pattern)
    + [Exercise 4](#exercise-4)
    + [Challenge 4](#challenge-4)
  * [Pattern 5: Mediator Pattern](#pattern-5--mediator-pattern)
    + [Exercise 5](#exercise-5)
    + [Challenge 5](#challenge-5)
  * [Pattern 6: Memento Pattern](#pattern-6--memento-pattern)
    + [Exercise 6](#exercise-6)
    + [Challenge 6](#challenge-6)
- [Java Design Patterns: Behavioral Part 2](#java-design-patterns--behavioral-part-2)
  * [Pattern 7: The Observer Pattern](#pattern-7--the-observer-pattern)
    + [Exercise 7](#exercise-7)
    + [Challenge 7](#challenge-7)
  * [Pattern 8: The State Pattern](#pattern-8--the-state-pattern)
    + [Exercise 8](#exercise-8)
    + [Challenge 8](#challenge-8)
  * [Pattern 9: The Strategy Pattern](#pattern-9--the-strategy-pattern)
    + [Exercise 9 (+9b)](#exercise-9---9b-)
    + [Challenge 9](#challenge-9)
  * [Pattern 10: The Template Method Pattern](#pattern-10--the-template-method-pattern)
    + [Exercise 10](#exercise-10)
    + [Challenge 10](#challenge-10)
  * [Pattern 11: The Visitor Pattern](#pattern-11--the-visitor-pattern)
    + [Exercise 11](#exercise-11)
    + [Challenge 11](#challenge-11)
- [Java Design Patterns: Structural](#java-design-patterns--structural)
  * [What are structural design patterns?](#what-are-structural-design-patterns-)
    + [Types of structural design patterns](#types-of-structural-design-patterns)
  * [Pattern 1: The Adapter Pattern](#pattern-1--the-adapter-pattern)
    + [Exercise 1](#exercise-1-2)
    + [Challenge 1](#challenge-1-1)
  * [Pattern 2: The Bridge Pattern](#pattern-2--the-bridge-pattern)
    + [Exercise 2](#exercise-2-1)
    + [Challenge 2](#challenge-2-1)
  * [Pattern 3: The Composite Pattern](#pattern-3--the-composite-pattern)
    + [Exercise 3](#exercise-3-1)
    + [Challenge 3](#challenge-3-1)
  * [Pattern 4: The Decorator Pattern](#pattern-4--the-decorator-pattern)
    + [Exercise 4](#exercise-4-1)
    + [Challenge 4](#challenge-4-1)
  * [Pattern 5: The Façade Pattern](#pattern-5--the-fa-ade-pattern)
    + [Exercise 5](#exercise-5-1)
    + [Challenge 5](#challenge-5-1)
  * [Pattern 6: The Flyweight Pattern](#pattern-6--the-flyweight-pattern)
    + [Exercise 6](#exercise-6-1)
    + [Challenge 6](#challenge-6-1)
  * [Pattern 7: The Proxy Pattern](#pattern-7--the-proxy-pattern)
    + [Exercise 7](#exercise-7-1)
    + [Challenge 7](#challenge-7-1)
  * [Further Reading](#further-reading)

# Java Design Patterns: Creational
[LinkedIn course](https://www.linkedin.com/learning/java-design-patterns-creational) by [Bethan Palmer](https://www.linkedin.com/learning/instructors/bethan-palmer)

## What are creational design patterns?
 - Used to abstract the process of instantiating objects, when the system should not be aware of how objects are created: they encapsulate the object creation code. They become more useful the larger & more complex our application becomes.
 - They are about defining a small subset of behaviors that can be used for the basis of lots more complex behaviors
 - Themes defining all creational design patterns:
   - they encapsulate knowledge about which concrete class the system should use
   - they conceal how objects are created and put together.

## Pattern 1: The Builder Pattern
 - Used when constructors are expected to be too complex, e.g. with a long list of parameters (wrong order of arguments may be given or sometimes not all information is required in the creation of an object)
 - Used instead of the **telescoping constructor pattern**, aka having a large selection of possible constructors for each object (aka with all possible & useful combinations of parameters) while retaining the flexibility of our code

### Exercise 1
We have the class `Bedroom` containing 8 fields and the `Architect` class which manages the `main` class which creates `Bedroom` objects. Use the Builder Pattern in order to add flexibility to the app.

Solution: 

a. [Simple] We create the `BedroomBuilder` class which contains setters for all `Bedroom` fields & the `createBedroom` method. The architect class now uses this builder's setters in order to specify whichever field we wish to set, and the rest are left with the default value (null). If this is not desirable, we may add a default value to the fields. I have added the logging in the main app & the `toString()` method for `Bedroom` in order to verify the results.

b. [Complete] We expand the functionality of the app by adding the ability to create more types of rooms. We extract the `Builder` interface.

c. [Complex] We expand the app in order to create houses with rooms (via `RoomBuilder`) and they can also have multiple stores. We expand the builder in order to facilitate all of the aformentioned functionalities.

## Pattern 2: The Singleton Pattern

Used when we need to make sure only one instance of a class can be created (e.g. Windows managers, DB connectors, File managers, UI dialogs, resource allocators & spoolers). The Java API already uses this pattern in some of its classes (e.g. `System`, `Desktop` and `Runtime`)

### Exercise 2a
In the `PrintSpooler` class we have a private constructor, thus not allowing any other class to initialize it. We also have the private method `init()` which would handle a more complex initialization process, and the method `getInstance()` which fetched the unique instance of `PrintSpooler` of our app.

### Exercise 2b
Use the Singleton pattern in a multithreaded app.

Solution: make the `getInstance()` method `synchronized`.

### Exercise 2c
Java's API of `SingletonList`, `SingletonSet` and `SingletonMap` can assist in the implementation of this pattern. Using these methods does not turn the collection into a singleton, but it does provide a single point of access that always returns the same instance.

In this application, we wish to implement a network connector of resources.

## Pattern 3: The Prototype Pattern

Makes copies of one original object.

Useful when...
 - we wish to create an object similar to one already created
 - creating a new instance is a memory intense process (faster app, shorter & cleaner code)
 - we want to keep the app agnostic to how an object is created
 - classes are loaded dynamically

This allows for cloned entities to still be modified.

Elements:
 - abstract prototype class, with a `clone()` method.
 - concrete implementations which override the `clone()` method.

### Exercise 3a
We use an app which simulates rabbits breeding. We use the `Cloneable` interface provided by Java and override the `clone()` method. When we run the main process we see that the original and the clone rabbit both have the same age.

However, the `clone()` method belongs to `Object`, not `Cloneable`. An alternative to this interface is the use of copy constructors. We could also just implement our own `clone()` method. Secondly, the `clone()` method only creates a shallow copy, meaning if a class contains mutable values, problems will arise.

*Note: It is worth reading [Effective Java](https://www.goodreads.com/book/show/34927404-effective-java) by Joshua Bloch for more info about the issues of this interface.*

### Exercise 3b
We add the field `Person owner` to the `Rabbit` class (a mutable object) and overcome the aforementioned issue. 

## Pattern 4: The Factory Method Pattern

Used when a class (`candyStore`) doesn't know exactly what object types (`candy`) need to be created.

We add the factory class which handles deciding which class to return, thus keeping the other classes immutable if another type of objects needs to be handled by the `candyStore` class, adding maintainability to the code.

### Exercise 4a
Given a candy store simulation app, use the aforementioned pattern in order to ameliorate the code.

### Exercise 4b

Introduce hierarchy.

### Exercise 4c

The full example.

## Pattern 5: The Abstract Factory Pattern

Provides an interface for creating families of objects, without specifying what their concrete typea are.

Useful when there is a system that creates objects, but how these objects are created should be hidden from view. (families of objects), e.g. bike parts for different types of bikes.

![The bike parts example as a graph](https://github.com/ZapDos7/design-patterns-examples/blob/master/bike-graph.png?raw=true)

This pattern improves consistency, as all bikes are created with the same parts, albeit different types of them.

### Exercise 5a
Start of the implementation.
### Exercise 5b
End result of the implementation.

### Exercise 5c
Make the above implementation extensible.

# Java Design Patterns: Behavioral Part 1
[LinkedIn course](https://www.linkedin.com/learning/java-design-patterns-behavioral-part-1) by [Bethan Palmer](https://www.linkedin.com/learning/instructors/bethan-palmer)

## What are behavioral design patterns?
- They are about how objects assign responsibilities between each other/how objects are connected & how they communicate & how responsibilities are assigned between them.

## Types of behavioral design patterns:
1. Class patterns (`isA` relationships)
   - how classes share responsibilities between themselves
   - they use inheritance
2. Object patterns (`hasA` relationships)
   - the most common type
   - how different object interact w/ each other
   - sometimes they help different objects work together in order to perform a task
   - sometimes they delegate requests to other objects
   - they use composition.

## Pattern 1: Chain of Responsibility
- Used when it is decided in runtime which entity handles a request.
- Passes along a request until it is handled
- Decouples the sender from the receiver
- Example use cases:
  - handling authentication
  - servlet filters for handling HTTP requests
  - context-dependent buttons in UI
- What to watch out for:
  - circular chains of requests
  - requests may never be handled
  - confusing stack traces

### Exercise 1
1. We define the abstract class `DocumentHandler` which later on will be implemented for each document type we wish to handle. This handler has a `DocumentHandler` field named `next`, indicating the next handler. This class handles the next handler, as we do not know which type the next handler might be each time.
2. We then define the other handlers, e.g. `SlideshowHandler`, `SpreadsheetHandler` and `TextDocumentHandler`. These implement a method named `openDocument()` which checks the document's extension and simply log whether they can handle this document or not.
3. We also create the `Client` class, which handles the main function. In the following line:
```
DocumentHandler chain = new SlideshowHandler(new SpreadsheetHandler(new TextDocumentHandler(null)));
```
we define the successor chain starting with a slideshow handler and ending with a text document handler. We then can add another handler if we need to handle another type of documents as the argument of the innermost constructor (here, `TextDocumentHandler`), after we implement said handler. 

### Challenge 1
Implement request handling using the same design pattern.

## Pattern 2: The Command Pattern
 - Useful when it is unknown *what is requested* or *what is receiving the request*.
 - Encapsulate a request inside an object
 - Decouples the object that invokes the command from the object that knows how to handle it.
 - Useful for commands we wish to perform later on, e.g.:
   - Support undo/redo functionality
   - Queueing/logging requests to be performed at different times

### Exercise 2
Goal: Decouple BE functionality from FE (button clicking)

Starting:
 - GUI class: hold simple information for UI, also holds the main method.
 - Button (with a `click()` method) - the invoker
 - Document (will hold the functionality of printing/saving documents) - the receiver.

We then add the `Command` interface and its implementations for `SaveCommand` and `PrintCommand`.

### Challenge 2
Implement order handling using the same design pattern.

## Pattern 3: Interpreter Pattern
Use Cases:
 - write custom regular expressions
 - write custom compiler
 - translate human languages
 - parse SQL
 - create a simple calculator
Key points:
 - express a recurring problem as a sentence & interpret it
 - define grammar
 - build an abstract syntax tree
Components:
1. `Context` (what we handle, e.g. a `String`)
2. Abstract `Expression` (defines a method `interpret(context)`)

   Two possible implementations:
   1. Terminal expression (the last time `interpret()` gets called)
   2. Non terminal expression (calls the interpret method, which alters the context and then it passes it onto another expression until terminal expression)
3. `Client` which creates instances of expression to interpret.

Positives:
- easy to extend/implement the grammar
- works best with simple grammar (complex ones new a new expression class per new rule)

### Exercise 3
Implement a language interpreter which can also rename variables to meet Java conventions.

We create the `Expression` interface which defines the `interpret()` method & its implementations: `NameNotPrimitiveType`, `FirstLetterIsLowerCase`, `FirstLetterNotUnderscore`, which all handle their corresponding cases by altering the context. We can test this in the `Main` class.

Therefore we check that firstly the variable name does not begin with `_`, then that it doesn't start with a capital letter and lastly that it's not a primitive type.

### Challenge 3
Implement a language interpreter which checks sentences for a capital first letter, no repeated words and that verifies that they end with a period.

## Pattern 4: Iterator Pattern
Example uses: `Collections` class with `forEach` loops

Benefits: agnostic as to the type of collection, as long as it implements `Collection`.

The `iterator` is a seperate object which is responsible for moving along the list, keeping track of which elements have been traversed already.

### Exercise 4
Create an iterator in order to print only the items that are in stock.

### Challenge 4
Create an iterator in order to print the names of the employees.

## Pattern 5: Mediator Pattern
Loosely coupled objects communicate through the mediator.

### Exercise 5
Given the existing implementation for the e-commerce site, implement the mediator pattern in order to introduce loose coupling onto the app. At the beginning, we notice that there is a circular dependency, as the `ECommerceSite` has a `Customer` field and vice versa.

How we do this: we implement the `Mediator` class containing a field for each object in our app (`Customer`, `ECommerceSite` & `Driver`). We there create the method `buy()`. We also decouple the existing classes. We also alter the `Main` class accordingly, using the `Mediator`'s method.

### Challenge 5
Simplify the airport application using the Mediator Pattern in order to decouple the objects and ameliorate the code.

## Pattern 6: Memento Pattern

Without breaking the principle of encapsulation, we wish to retain & externalize the previous state of an object in order to implement e.g. the undo functionality.

Terms:
 - Originator: the object whose states we wish to retain
 - Caretaker: the object changing the state of the originator
 - Memento: the object between the two which handles the state change

Notes:
 - If the originator contains a lot of data, this pattern increases the memory usage (so it is might be best to omit it)

 ### Exercise 6
 Goal: Add `save` and `undo` operations onto a document handling app.

 Beginning: The `TextDocument` which `write`s and `print`s the text and the `DocumentViewer` class which also contains the `main` method.

 Solution: We add the `Memento` class which contains the `state` field, we add a `Memento` field to the `TextDocument` class, and we also add there the methods to `save()` and `undo()` which utilize the pattern. We update the `main` method accordingly.

 ### Challenge 6
 Similarly, implement the memento pattern in order to handle the calculator app state.

 # Java Design Patterns: Behavioral Part 2
[LinkedIn course](https://www.linkedin.com/learning/java-design-patterns-behavioral-part-2) by [Bethan Palmer](https://www.linkedin.com/learning/instructors/bethan-palmer)

## Pattern 7: The Observer Pattern
Useful in OOP projects where many classes need to interact with each other without being tightly coupled; when many classes need to be notified of changes on another object.

Elements:
 - the subject/the observable object
 - the observer(s), which watch the object

*Note:* Prior to Java 9 there was the [`Observer`/`Observable` classes](https://docs.oracle.com/javase/9/docs/api/java/util/Observable.html#:~:text=Class%20Observable&text=Deprecated.,for%2Done%20correspondence%20with%20notifications.), but have since been deprecated, since they did not log enough information on the updates on the subject. Instead, it is recommended to use `PropertyChangeListener` and `PropertyChangeSuppport` classes.

### Exercise 7
A simple social media platform which notifies one's connections when one updates their status, showing that update on their feed.
 - `Connection` represents the connection with another user, with a `status` String field (*observable*)
 - `SocialMediaFeed` represents our feed, with a `statuses` List of String field (*observer*)
 - `Main` which contains the main class. Initially it prints nothing as the elements are not observing each other
### Challenge 7
Use the observer pattern to refactor an app which handles updates in traffic for various cities.
## Pattern 8: The State Pattern
Allows objects to alter their behaviour depending on their state (e.g. play/pause button) simplifying the otherwise required if/else blocks we could use for this issue.

The `state` is seperated out from the client and is usually an interface, with concrete implementations for different states, which handle the behaviour based on the different state of the item.
### Exercise 8
We implement a media player app with the state pattern.
The `MediaPlayer` class contain the fields `state` and `icon` & the `Main` class handles the changes.

We create the `State` interface and we define the `pause()` and `play()` methods, with a `MediaPlayer` argument each. We then implement the `PlayingState` and the `PausedState`. We add a `State` field to the `MediaPlayer` class & also alter the `play()` & `pause()` methods.
### Challenge 8
Similarly, refactor an app handling a fan's temperature. Note that the fan cannot go from low to high immediately, meaning we need to use the medium setting in between.
## Pattern 9: The Strategy Pattern
Define a family of algorithms used dynamically selected based on whichever state we are. (e.g. different file encryption methods, different validation methods, different sorting algorithms, saving different file types etc)

 - `context` which maintains a reference to the strategy objects
 - `strategy` as an interface and its concrete implementations (which are not needed as of Java 8 - see below)
### Exercise 9 (+9b)
Implement the above pattern on an app handling various encryption methods.
### Challenge 9
Refactor an application handling customer payments with various ways.

## Pattern 10: The Template Method Pattern
A superclass defines the (common) steps of an algorithm and the subclasses redefine some of these steps. This solves code duplication.

It is important to note:
 - it can be difficult to communicate intent to users
 - it makes the program flow harder to follow/more complex
### Exercise 10
Use the above pattern in order to remove duplicate code when printing two slightly different pizza recipes.
### Challenge 10
Use the above pattern in order to remove duplicate code for a simple RPG game.
## Pattern 11: The Visitor Pattern
A visitor object handles the communication between objects.

Having an interface with concrete implementations, we wish to apply some operation to each implementation, slightly different for each one. We could create a method to accept visitors in each implementation (defined in the interface) but this might be harder to understand or make changes to. Instead, we can create a Visitor interface, defining a visit method for each of the concrete implementations.

Highly useful when having a composite or list of other elements. Best used when the elements are *not* likely to change.

It's fairly complext & for specific only use cases, so it's scarce to be used.

It makes use of the open-closed principle.
### Exercise 11
The `Groceries` interface is extended by `Milk` and `Bread`, with `getPrice()` and `setPrice()` methods. We also have the `GroceryList` class which `implements Groceries` and has a `ArrayList<Groceries> groceries` field. This returns the sum of the prices of all groceries in the list. The `Client` handles the main process.

Our goal is to apply a discount on all groceries, without altering the `GroceryList` class, as it does not need to be affected by this.

1. We create a `Visitor` interface with `visit()` methods for each implementation of `Groceries` as well as the interface itself. We implement the methods in the `DiscountVisitor` implementation of `Visitor` and alter the main process accordingly.
2. We add the `accept()` methods in the `Groceries` interface & the implementations (`Milk`, `Bread`, `GroceryList`) and update the main process accordingly.
### Challenge 11
Use the Visitor pattern in order to refactor an app calculating employees salaries.

# Java Design Patterns: Structural
[LinkedIn course](https://www.linkedin.com/learning/java-design-patterns-structural) by [Bethan Palmer](https://www.linkedin.com/learning/instructors/bethan-palmer)

## What are structural design patterns?

 - Design patterns refering to how classes and objects are structured & used together to form larger structures. 

### Types of structural design patterns
1. Class Patterns (`isA`)
    - They are focused on how classes are structured & interact.
    - They focus on inheritance
2. Object Patterns (`hasA`)
    - They are focused on how we use objects
    - They allow objects to change behavior at runtime.

## Pattern 1: The Adapter Pattern

It helps when we need to adapt a class from a e.g. third-party app to our own app's needs. We simply create the adapter interface to bridge the gap.

*Fun fact! There are some examples of this pattern in the JDK itself. For example, the collections class has two methods lists and enumeration, which use the adapter pattern to provide compatibility with Legacy APIs that work with the enumerations. Another example is the as list method of the arrays class, which uses the adapter pattern to allow array based and collection based APIs to work together.*

### Exercise 1
The app calculates prices of different types of vehicles.

At first we have the `PriceCalculator` interface with the `calculatePrice()` method, with two implementations (`CarPriceCalculator` and `TruckPriceCalculator`) (the formulas are random, simple ones for the sake of the example). The main class simply calculates & prints these prices.

These prices are all in USD. Within the `lib` folder, we have `uk-car-price-calculator.jar` (also as a dependency in out `pom`). Through its JavaDocs we can see that it has a class (`UKCarPriceCalculator`) with a constructor and a `getPrice()` method.

Solution: We create an `Adapter` class implementing the `PriceCalculator` interface with a field `UKCarPriceCalculator`. We create a constructor and we override the `calculatePrice()` method.

### Challenge 1
Implement the aforementioned pattern in order to ameliorate the app printing city temperatures around the globe, therefore handling Fahrenheit as well as Celsius.

## Pattern 2: The Bridge Pattern

Separates hierarchy: e.g. we have shapes (circle, triangle) which can be red and blue. Then we add the colour green, so we have to add new code in both shapes. If we desire to alter the red implementation, we alter all reds. If we add a new shape, we have to add all the colours again, etc - we differentiate the shape and the colour in different classes/trees. Now, when we add a new colour-shape combo, we use the existing, corresponding implementations (e.g. for blue & for triangle), instead of writing anew (largely duplicate) code.

### Exercise 2
Goal: Simplify the shapes & colours canvas app with the above pattern.

Tip: Some IDEs can display the class relationships in a diagram, e.g. [IntelliJ](https://www.jetbrains.com/help/idea/class-diagram.html#analyze_class).

### Challenge 2

Refactor an app that draws buttons in a similar manner.

We find that the buttons defined at the start of this challenge are named `Size` `Type` `Button`, where size: small, medium or large & type: radio, dropdown or checkbox.

We therefore need to introduce the interface `ButtonSize`. We then remove the useless classes like `SmallCheckboxButton` & refactor the existing classes.

## Pattern 3: The Composite Pattern

**Varargs** in Java: methods whose argument is in this format: `method(Type... fieldName)`; this means when calling this method, we can pass as argument any amount of `Type` arguments.

This is used when we want to treat single objects & groups of objects in the same manner, or when we have code that is very similar/identical to handle different types of objects.

### Exercise 3

We have an app managing a company's expenses:
 - `Manager` has a field `name` and a method `payExpenses(int amount)` which prints that the person with name `name` has been paid `amount` dollars.
 - `Salesperson` has a field `Manager` and a field `name` & a similar `payExpenses()` method
 - `SalesTeam` has two lists, one of `Manager`s and one for `Salesperson`s and, again, the similar `payExpenses()` method.

We can refactor these classes in order to unify the identical `payExpenses()` methods and reduce duplicate code.

We add the `Payee` interface which defines the identical method. Now, `Manager`, `Salesperson` & `SalesTeam` all implement it.

### Challenge 3

Refactor similarly an app which simulates books checkouts & returns.

## Pattern 4: The Decorator Pattern

It is used when:
 - we wish to add additional responsibilities to an object *dynamically*
 - we want more flexibility than subclassing allows

Basically, we have the interface and some implementations. When we wish to add traits onto one implementation, we encapsulate it into another.

### Exercise 4

Given a canva app which paints circles, we wish to add the functionality of drawing circles with red borders.

Solution: We add the interface `ComponentsWithRedBorder` which `implements Component` and alter the `draw()` method accordingly. Then, in our `Canvas` class, we decorate the desired circle (e.g. `circle2`)

### Challenge 4

Refactor a pizza ordering app similarly, in order to facilitate users desiring extra cheese on their pizza's toppings.

## Pattern 5: The Façade Pattern

Hide complexity behind an interface, in order to simplify user experience.

Benefits:
 - makes it easier to use complex code
 - promotes loose coupling
 - it is not enforced - user can interact with the complex classes hidden behind the façade, if needed.

### Exercise 5

We have an app which manages vacations (car rentals, hotel bookings & flight arrangements). With the façade pattern, we can unify the client's many calls of methods into one which simply books the entire vacation's details.

Solution: We create the façade class which handles the same functionality & update our main process.

### Challenge 5
Refactor a driving car app similarly.
- classes `Accelerator`, `Clutch`, `GearStick`, `Handbrake` & `Ignition` hold info as well as functions for each car part & its actions
- `Car` class handles the main process which calls upon the methods needed in order to drive a car.
## Pattern 6: The Flyweight Pattern
Useful when an app uses resources heavily, solves the issue of `java.lang.OutOfMemory` errors.

Also can maximize performance when creating a new object.

e.g. when typing a document, instead of creating a new `char a = 'a';` each time the user types the letter `a`, we reuse the same one.

**Intrinsic vs Extrinsic State** 
> *Intrinsic state is stored in the flyweight; it consists of information that's independent of the flyweight's context, thereby making it sharable. Extrinsic state depends on and varies with the flyweight's context and therefore can't be shared.* - [source](https://www.cs.unc.edu/~stotts/GOF/hires/pat4ffso.htm)

So, in the letter example, intrinsic state refers to the character code (same for all objects) whereas extrinsic state to the position in page (different for every object).

Flyweight objects allow to share the intrinsic states, so we reuse that, and the extrinsic state's info can be passed to the flyweight object when it needs it.
### Exercise 6

We have an app which predicts traffic.

Classes:
 - `Vehicle` interface with `getType()`, `getLocation()`, `setLocation()` methods
 - its implementations: `Car`, `Truck`
 - `TrafficSimulator` which holds the main process

Solution:
1. Create `VehicleFactory` class to depict the flyweight object. Within it, we have `HashMap` of `Vehicle`s which hold the info for each vehicle. We check if a vehicle object of the specified type already exists; if it does, we handle it, otherwise we create a new one.
2. We add the factory to the main process, & when creating a new vehicle, we call its `getVehicle()` method implementing the aforementioned functionality.
### Challenge 6

Refactor an animal population simulation app similarly.

## Pattern 7: The Proxy Pattern

*Virtual* proxies are used to save memory & improve performance. We create a proxy of an item when we want to access the item's *inexpensive* operations (e.g. `getWidth()`, `getHeight()` of an `image`) and we access the actual thing when we **need** the *expensive* operations (e.g. `loadImageFromDisk()`) - lazy loading.

Common uses:
 - representation of large objects in GUI,
 - representation of expensive db ops
 - protection proxies for authentication of access

### Exercise 7

Given an app which displays images like a slideshow, refactor using the Proxy Pattern.

We have the interface called `DisplayObject` which holds the `display()` method, and the class `ImageFile` implementing it. Lastly, in `ImageGallery` we call these methods in order to display images from the `resources` folder.

The `load()` method in `ImageFile` is an expensive process consuming memory & time, and it's our refactoring goal.

Solution: We create the `ImageProxy` class implementing `DisplayObject` with two fields, the image path and the actual imageFile, and an ameliorated `display()` method which checks if the file already exists. We also alter our main process accordingly.

### Challenge 7

Similarly refactor an app which handles a super market's inventory. The items are stored in a `List`, however in a real world scenario it would be a database, and thus accessing it would be even more costly. The issue here lies in the fact that `Main` we create the inventory at the start of the program but only access it at the end, and we could even never access it at all. We refactor the app in order to reduce memory usage & improve start up time, by not having the inventory be created there.

## Further Reading
 - [Design Pattern Catalog](https://java-design-patterns.com/patterns/)