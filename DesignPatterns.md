# [Design Patterns](https://refactoring.guru/design-patterns/catalog)

##### A briefly explanation for the main design patterns in my view.

---

## [Factory method](https://refactoring.guru/design-patterns/factory-method)

In order to create a program that supports multiple extensions and more methods inside you will create a base class or a base interface that will contain the common functions and fields for what you want to create and inside the components that will extend your interface/baseclass you will override the functionalities needed to be changed.

How to implement it?
- declare a common interface for all objects
- inside the individual objects declare the custom functionality
- create the creator class that can create custom objects depending on how it is called.
- concrete creators - override the base creator in order to create custom objects

For the dialog example:
- there is the dialog base creator that offers the base dialog functionalities
- there are small classes for each windows and HTML buttons that adds custom designs and functionalities for each button

Why use the factory method?
- scalability
- easy to extend subclasses
- besides creating new objects you can implement it to reuse old ones

Ups and downs:
- UP- Respects single responsibility principle
- UP - open/closed principle
- DOWN - A lot of classes will be created for each new functionality or objects

---

## [Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory)

The utility is that you can create a general abstract class that implements the basic properties of an object and later you can expand those in different classes in classes that will have specific properties and functionalities for those.

For instance, for a chair, you can have a base class where you define the base functionalities and later you can create classes from that class that will implement concrete designs and more advanced functionalities like tiers or comfortable handle 

Properties:
- It allows you to create groups of objects that are designed to work together
- It makes it easier to add new types of objects in the future, without having to make changes to the code that uses them
- It decouples the code that creates objects from the code that uses them, making it easier to change the objects being used without affecting the rest of the code

Upsides of using this pattern:
- Respect open/closed principle
- Respects the single responsibility principle
- You will avoid coupling between products
- The products will be compatible with each other

Downsides:
- the code will be hard to maintain
- When a new family of objects will appear there will be new code to write in order to add a new class
- There may be a result of duplicated code in some parts

---

## [Builder](https://refactoring.guru/design-patterns/builder)

This method lets you create different types and representations of an object with the same construction code

- The implementation of a builder suggests extracting all the functionalities in a class with different objects that are called builders. 
- By doing the separation mentioned above you can call only the builders that you need to construct the object that will help you.
- You can also create directors to reuse the code and execute the builders in order.
- The downside of using builders is that the class that will have all the builders will grow when new functionalities are added
- Upside - reusability

---

## [Prototype](https://refactoring.guru/design-patterns/prototype)

- create an interface and from that interface create multiple classes for each type of object that you need.
- You just clone the config that you want for your new object
- It is easier to create similar objects without having to create them from scratches
- Downsides:
    - big complexity when new functionalities are added
    - hard to understand in a big project

---

## [Singleton](https://refactoring.guru/design-patterns/singleton)

- ensures that there is only one instance of the object and everything points to that
- whenever the method from singleton is called, the result will always be the same
- the singleton will only be created once and altered within the program
- it will have private fields but the functions will be public
- the awful downside is that when testing it, mocked values for that class won’t be created with different values to cover multiple cases
