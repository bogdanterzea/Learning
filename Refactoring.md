# Refactoring

## [Code smells](https://refactoring.guru/refactoring/smells)

### [Bloaters](https://refactoring.guru/refactoring/smells/bloaters)
- code methods or classes that got very big and hard to read and understand

#### Long methods
- a method that got too many lines of code should raise questions.
    - Problem:
        - that method is improved and code is added inside but the code is never deleted from that method.
    - Solving:
        - extract code in smaller functions
        - Move expressions which makes calculs inside a function and return directly the result. Don't use temporary variables for that
        - Don't take apart an object to get different values and send them in other functions. Send the entire object.

#### Large Class
- in time, if developer doesn't pay attention, some classes may grow too big.

    - Problem:
        - classes get bigger and bigger as the program evolves.
        - developer is using same class instead of using a new one.
    - Solving:
        - when a class contains more data than it needs, it may be spitted in more classes.
        - when some features from a class are used only in specific cases, create subclasses of that class and use it in specific cases
        - if a part of interface is identical in two classes, it can be extracted into a separate class.

#### Primitive Obsession
- How it appears:
    - programmer may use a field/variable to solve a temporary problem and forgets about it
    - many static strings or integers to make checks or test stuff
- Solving:
    - logically group primitive fields inside their class and move their associated behavior inside that class too.
    - try to make the code more flexible and use objects instead of primitives

#### Long Parameter List
- How it happens:
    - when someone moves different methods to create objects in other
    - passing a list of parameters to a method instead of using a simple object with all that data.
- Solving:
    - instead of passing a long list of parameters, send an object with all the data for the method where it is used.

#### Data Clumps
- How it appears:
    - Different parts of code having identical groups of variables/parameters of functions
    - Copy-pasted code with similar functionality for a feature that existed before.
- Solving:
    - Create classes and include common fields inside of them
    - if more data is passed in other methods then create an object with all that data and use it.


### [Object-Orientation abusers](https://refactoring.guru/refactoring/smells/oo-abusers)

#### Switch statements:
- How it appears:
    - handling a lot of cases in a single function with a switch
- Solving:
    - if inside the switch is used mostly the same function with different parameters, create different functions for those parameters and remove or change the switch accordingly.
    - if it's possible move it inside the right class; where it is used the most.
    - use null as a default if one of switch cases returns a null object.

#### Temporary field:
- How it appears:
    - if a developed doesn't want to create a function with large amount of inputs he will create a class with more fields to cover all that data. maybe that data is specific only inside some function and in rest is useless.
- Solving:
    - All the temporary fields can be extracted in their own class;
    - Use null for unused temporary objects.

#### Refused Bequest:
- How it appears:
    - wrong inheritance;
    - functions left unused because of wrong inheritance
- Solving:
    - eliminate the inheritance if the subclass has nothing in common with superclass.
    - find the common fields and methods of classes and create a superclass for both of them only with both common data.

#### Alternative classes with different interfaces:
- How it appears:
    - two classes doing the same thing but with different namings. The programmer may not know that those functionalities already existed.
- Solving:
    - make all namings clear and describe exactly what it does.
    - extract common used code inside a superclass for both classes.
    - delete one of the classes if the code is all duplicated and if you can incorporate everything inside one class.

### [Change preventers](https://refactoring.guru/refactoring/smells/change-preventers)

#### Divergent charge:
- How it appears:
    - when something small needs to change, the developer has to change a lot of data in a lot of methods and classes.
    - a lot of copy-pasted code-poor programming :(
- Solving:
    - Create inheritance between classes to reduce duplicated code and have a better control over them.

#### Shotgun surgery
- How it appears:
    - a single responsability splited up inside more classes
- Solving:
    - move the behaviors where those are mostly used and try to clean overcharged classes.
    - if a class remains almost empty, maybe is better to find a solution to get rid of it.

#### Hierarchies:
- How it appears:
    - creating a lot of subclasses of subclasses when new features appears inside the app.
- Solving:
    - Extract all duplicated code inside a superclass and if it's possible remove all empty/poor used subclasses.

### [Dispensables](https://refactoring.guru/refactoring/smells/dispensables)

#### Comments:
- How it appears:
    - all comments appears where developers thinks the code it's hard to understand
- Solving:
    - Better naming of functions or variables; Make them self-explanatory
    - if a comment describes what some lines of code does; just move those lines in a function and name that function with what action happens in there.
    - make the code more intuitive...not long and covered with comments

#### Duplicate Code:
- How it appears:
    - When more programmers develop similar functionalities
    - Wrong naming for functions with same functionality
    - "Novice rush"-> copy-paste existing parts to make a similar functionality, instead of creating a superclass for common functionalities.
- Solving:
    - Extract methods for similar code, and call that method in both places with different parameters
    - if two subclasses have same code, extract it in a superclass.
    - for duplicate code similar but not fully identical, move the identical code in a method and call it from there.

#### Lazy Class:
- How it appears:
    - When cleaning and refactoring code, some functions may become very small.
    - Classes that were defined for future development but never finished.
- Solving:
    - if a class is too small and does only one or two things; that functionality may be moved in another class.
    - for a subclass that does basically the same thing that already exists in it's superclass....just use the superclass functionality and remove the subclass.

#### Data Class:
- How it appears:
    - A newly created class that may contain only fields and no operations inside.
- Solving:
    - if inside the class are public fields, make them private and create getters and setters to access them
    - search where is that class accessed and maybe some functions that access that class may be encapsulated in that class
    - after you populate the class with specific functions, get rid of old functions that program used and use those from inside the class.

#### Dead code:
- How it appears:
    - Variables/parameters/fields/methods left unused after changes inside the project
- Solving:
    - Delete all unused things
    - Fix functions by removing parameter that is no longer needed

#### Speculative generality
- How it appears:
    - Parts of code created "just in case", for future.
- Solving:
    - Remove unused abstract classes
    - Remove unused methods
    - Delete useless fields
    - Delete extra parameters from functions

### [Couplers](https://refactoring.guru/refactoring/smells/couplers)

#### Feature envy
- Reason:
    - It appears when fields are moved to a data class. More method may access data from other object than it's own data.
- Solving:
    - Keep things in the same place, don't split them when changes occurs
    - If it's necessarily to move something like a method...make sure you take all dependencies with it. Or be sure you calculate everything.

#### Inappropriate intimacy
- Reason:
    - When a class has too much information about everything. Classes should be small and own their purpose only.
- Solving:
    - Don't keep code specific only for one class in it's superclass.

#### Message chains
- Reason:
    - When an object needs to return something from another object and that object from other object some data.
- Solving:
    - Think why that chain occurs; maybe you can extract data in a method or maybe the last object used may not do anything else and can be remove and that small data moved.

#### Middle man
- Reason:
    - Elimination of big portions of code.
    - Moving of a lot of data, letting a class only filled with a single call of other method.
- Solving:
    - Simply remove that middle-mad and call directly what you need.
