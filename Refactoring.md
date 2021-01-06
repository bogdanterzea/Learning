# Refactoring

## [Code smells](https://refactoring.guru/refactoring/smells)

### [Bloaters](https://refactoring.guru/refactoring/smells/bloaters) - code methods or classes that got very big and hard to read and understand

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
