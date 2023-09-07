# Abstract classes
Python is considered to be a very flexible programming language, but that <u>doesn’t</u>   mean that there are no controls to impose a set of functionalities or an order in a class hierarchy. When you develop a system in a group of programmers, it would be useful to have some means of establishing requirements for classes in matters of interfaces (methods) exposed by each class.

## What is an abstract class?
An **abstract class** should be considered a blueprint for other classes, a kind of contract between a <u>class designer</u> and a <u>programmer</u>:
- the class designer sets requirements regarding methods that must be implemented by just declaring them, but not defining them in detail. Such methods are called **abstract methods**.
- The programmer has to deliver all method definitions and the completeness would be validated by another, dedicated module. The programmer delivers the method definitions by <u>overriding</u> the method declarations received from the class designer.

This contract assures you that a child class, built upon your abstract class, will be equipped with a set of concrete methods imposed by the abstract class.

### Why do we want to use abstract classes?
The very important reason is: we want our code to be **polymorphic**, so all subclasses have to deliver a set of their own method implementations in order to call them by using common method names.

Furthermore, a class which contains one or more abstract methods is called an abstract class. This means that abstract classes are not limited to containing only abstract methods – some of the methods can already be defined, but if any of the methods is an abstract one, then the class becomes abstract.

### What is an abstract method?
An abstract method is a method that has a declaration, but does not have any implementation. We'll give some examples of such methods to emphasize their abstract nature.

Let's talk about an example:

Assume that you’re designing a music player application, intended to support multiple file formats. Some of the formats are known now, but some are not yet known. The idea is to design an abstract class representing a base music format and corresponding methods for “open”, “play”, “get details”, “rewind”, etc., to maintain polymorphism.

Your team should implement concrete classes for each format you'd like to support. Whenever new format specifications become available, you won’t have to rework your music player code, you’ll just have to deliver a class supporting the new file format, fulfilling the contract imposed by the abstract class.

Remember that it isn’t possible to instantiate an abstract class, and it needs subclasses to provide implementations for those abstract methods which are declared in the abstract classes. This behavior is a test performed by a dedicated Python module to validate if the developer has implemented a subclass that **overrides all abstract methods**.

When we’re designing large functional units, in the form of classes, we should use an abstract class. When we want to provide common implemented functionality for all implementations of the class, we could also use an abstract class, because abstract classes partially allow us to implement classes by delivering concrete definitions for **some of the methods, not only declarations**.

We have just defined the means by which to provide a common Application Program Interface (API) for a set of subclasses. This capability is especially useful in situations where your team or third-party is going to provide implementations, such as with plugins in an application, even after the main application development is finished.

Let's start with a typical class that can be instantiated:
```python
class BluePrint:
    def hello(self):
        print('Nothing is blue unless you need it')
bp = BluePrint()
bp.hello()
```
There’s nothing new for you here – it’s just an example of creating a class and instantiating it. No errors, no doubts, and it gives a clear output:
```
Nothing is blue unless you need it
```
Python has come up with a module which provides the helper class for defining Abstract Base Classes (ABC) and that module name is `abc`.

The ABC allows you to mark classes as abstract ones and distinguish which methods of the base abstract class are abstract. A method becomes abstract by being decorated with an `@abstractmethod` decorator.
```python
import abc

class BluePrint(abc.ABC):
    @abc.abstractmethod
    def hello(self):
        pass

class GreenField(BluePrint):
    def hello(self):
        print('Welcome to Green Field!')


gf = GreenField()
gf.hello()
```
To start with ABC you should:
- import the `abc` module;
- make your base class inherit the helper `class ABC`, which is delivered by the `abc` module;
- decorate abstract methods with `@abstractmethod`, which is delivered by the `abc` module.

    When you run the code, the output doesn’t surprise anyone:
    ```
    Welcome to Green Field!
    ```
So far everything works fine, so let's play with the code a little.

Now we'll try to instantiate the `BluePrint` class:
```python
import abc

class BluePrint(abc.ABC):
    @abc.abstractmethod
    def hello(self):
        pass

class GreenField(BluePrint):
    def hello(self):
        print('Welcome to Green Field!')
gf = GreenField()
gf.hello()

bp = BluePrint()
```
The output:
```
Welcome to Green Field!
Traceback (most recent call last):
(...)
    bp = BluePrint()
TypeError: Can't instantiate abstract class BluePrint with abstract methods hello
```
indicates that:
- it’s possible to instantiate the `GreenField` class and call the `hello` method, because the Python developer has provided a concrete definition of the `hello` method.

    In other words, the Python developer has overridden the abstract method `hello` with their own implementation. When the base class provides more abstract methods, all of them must be overridden in a subclass before the subclass can be instantiated.
- Python raises a `TypeError` exception when we try to instantiate the base `BluePrint` class, because it contains an abstract method.

Now we'll try to inherit the abstract class and forget about overriding the abstract method by creating a `RedField` class that does not override the `hello` method.
```python
import abc

class BluePrint(abc.ABC):
    @abc.abstractmethod
    def hello(self):
        pass

class GreenField(BluePrint):
    def hello(self):
        print('Welcome to Green Field!')

class RedField(BluePrint):
    def yellow(self):
        pass

gf = GreenField()
gf.hello()

rf = RedField()
```
The output:
```
Welcome to Green Field!
Traceback (most recent call last):
(...)
    rf = RedField()
TypeError: Can't instantiate abstract class RedField with abstract methods hello
```
indicates that:
- it’s possible to instantiate the `GreenField` class and call the `hello` method;
- the `RedField` class is still recognized as an abstract one, because it inherits all elements of its super class, which is abstract, and the `RedField` class does not override the abstract `hello` method.

### Multiple inheritance
When you plan to implement a multiple inheritance from abstract classes, remember that an effective subclass should override all abstract methods inherited from its super classes.

### Summary:
- Abstract Base Class (ABC) is a class that cannot be instantiated. Such a class is a base class for concrete classes;
- ABC can only be inherited from;
- we are forced to override all abstract methods by delivering concrete method implementations.

A note:
It’s tempting to call a module `abc` and then try to import it, but by doing so Python imports the module containing the ABC class instead of your local file. This could cause some confusion – why does such a common name as `abc` conflict with my simple module `abc`?

Run your own experiment to become familiar with the error messages you would encounter in such a situation.
