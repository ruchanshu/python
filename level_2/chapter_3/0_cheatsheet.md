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