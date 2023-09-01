## Summary

### Object-Oriented Programming
1. A **class** is an idea (more or less abstract) which can be used to create a number of incarnations – such an incarnation is called an **object**.
2. When a class is derived from another class, their relation is named **inheritance**. The class which derives from the other class is named a **subclass**. The second side of this relation is named **superclass**. A way to present such a relation is an **inheritance diagram**, where:
   - superclasses are always presented **above** their subclasses;
   - relations between classes are shown as arrows directed **from the subclass toward its superclass**.
3. Objects are equipped with:
   - a **name** which identifies them and allows us to distinguish between them;
   - a set of **properties** (the set can be empty)
   - a set of **methods** (can be empty, too)
4. To define a Python class, you need to use the `class` keyword. For example:
   ```python
   class This_Is_A_Class:
        pass
   ```
5. To create an object of the previously defined class, you need to use the class as if it were a function. For example:
   ```python
   this_is_an_object = This_Is_A_Class()
   ```
6. A **stack** is an object designed to store data using the **LIFO** model. The stack usually performs at least two operations, named `push()` and `pop()`.
7. Implementing the stack in a procedural model raises several problems which can be solved by the techniques offered by **OOP** (**O**bject **O**riented **P**rogramming):
8. A **class method** is actually a function declared inside the class and able to access all the class's components.
9. The part of the Python class responsible for creating new objects is called the **constructor**, and it's implemented as a method of the name `__init__`.
10. Each class method declaration must contain at least one parameter (always the first one) usually referred to as `self`, and is used by the objects to identify themselves.
11. If we want to hide any of a class's components from the outside world, we should start its name with `__`. Such components are called **private**.
12. An **instance variable** is a property whose existence depends on the creation of an object. Every object can have a different set of instance variables.

   Moreover, they can be freely added to and removed from objects during their lifetime. All object instance variables are stored inside a dedicated dictionary named `__dict__`, contained in every object separately.

13. An instance variable can be private when its name starts with `__`, but don't forget that such a property is still accessible from outside the class using a **mangled name** constructed as `_ClassName__PrivatePropertyName`.
14. A **class variable** is a property which exists in exactly one copy, and doesn't need any created object to be accessible. Such variables are not shown as `__dict__` content.

   All a class's class variables are stored inside a dedicated dictionary named `__dict__`, contained in every class separately.

15. A function named `hasattr()` can be used to determine if any object/class contains a specified property.
   For example:
   ```python
   class Sample:
       gamma = 0 # Class variable.
       def __init__(self):
           self.alpha = 1 # Instance variable.
           self.__delta = 3 # Private instance variable.
   
   
   obj = Sample()
   obj.beta = 2  # Another instance variable (existing only inside the "obj" instance.)
   print(obj.__dict__)
   ```
   The code outputs:
   ```
   {'alpha': 1, '_Sample__delta': 3, 'beta': 2}
   ```
16. A method is a function embedded inside a class. The first (or only) parameter of each method is usually named `self`, which is designed to identify the object for which the method is invoked in order to access the object's properties or invoke its methods.
17. If a class contains a **constructor** (a method named `__init__`) it cannot return any value and cannot be invoked directly.
18. All classes (but not objects) contain a property named `__name__`, which stores the name of the class. Additionally, a property named `__module__` stores the name of the module in which the class has been declared, while the property named `__bases__` is a tuple containing a class's superclasses.
   For example:
   ```python
   class Sample:
       def __init__(self):
           self.name = Sample.__name__
       def myself(self):
           print("My name is " + self.name + " living in a " + Sample.__module__)
   
   
   obj = Sample()
   obj.myself()
   ```
   The code outputs:
   ```
   My name is Sample living in a __main__
   ```
19. A method named `__str__()` is responsible for **converting an object's contents into a (more or less) readable string**. You can redefine it if you want your object to be able to present itself in a more elegant form. For example:
   ```python
   class Mouse:
       def __init__(self, name):
           self.my_name = name
   
   
       def __str__(self):
           return self.my_name
   
   
   the_mouse = Mouse('mickey')
   print(the_mouse)  # Prints "mickey".
   ```
20. A function named `issubclass(Class_1, Class_2)` is able to determine if `Class_1` is a **subclass** of `Class_2`. For example:
   ```python
   class Mouse:
       pass
   
   
   class LabMouse(Mouse):
       pass
   
   
   print(issubclass(Mouse, LabMouse), issubclass(LabMouse, Mouse))  # Prints "False True"
   ```
21. A function named `isinstance(Object, Class)` checks if an object **comes from an indicated class**. For example:
   ```python
   class Mouse:
       pass
   
   
   class LabMouse(Mouse):
       pass
   
   
   mickey = Mouse()
   print(isinstance(mickey, Mouse), isinstance(mickey, LabMouse))  # Prints "True False".
   ```
22. A operator called `is` checks if two variables refer to **the same object**. For example:
   ```python
   class Mouse:
       pass
   
   
   mickey = Mouse()
   minnie = Mouse()
   cloned_mickey = mickey
   print(mickey is minnie, mickey is cloned_mickey)  # Prints "False True".
   ```
23. A parameterless function named `super()` returns a **reference to the nearest superclass of the class**. For example:
   ```python
   class Mouse:
       def __str__(self):
           return "Mouse"
   
   
   class LabMouse(Mouse):
       def __str__(self):
           return "Laboratory " + super().__str__()
   
   
   doctor_mouse = LabMouse();
   print(doctor_mouse)  # Prints "Laboratory Mouse".
   ```
24. Methods as well as instance and class variables defined in a superclass are **automatically inherited** by their subclasses. For example:
   ```python
   class Mouse:
       Population = 0
       def __init__(self, name):
           Mouse.Population += 1
           self.name = name
   
       def __str__(self):
           return "Hi, my name is " + self.name
   
   class LabMouse(Mouse):
       pass
   
   professor_mouse = LabMouse("Professor Mouser")
   print(professor_mouse, Mouse.Population)  # Prints "Hi, my name is Professor Mouser 1"
   ```
25. In order to find any object/class property, Python looks for it inside:
    - the object itself;
    - all classes involved in the object's inheritance line from bottom to top;
    - if there is more than one class on a particular inheritance path, Python scans them from left to right;
    - if both of the above fail, the `AttributeError` exception is raised.
26. If any of the subclasses defines a method/class variable/instance variable of the same name as existing in the superclass, the new name **overrides** any of the previous instances of the name. For example:
   ```python
   class Mouse:
       def __init__(self, name):
           self.name = name
   
       def __str__(self):
           return "My name is " + self.name
   
   class AncientMouse(Mouse):
       def __str__(self):
           return "Meum nomen est " + self.name
   
   mus = AncientMouse("Caesar")  # Prints "Meum nomen est Caesar"
   print(mus)
   ```
