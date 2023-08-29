## Summary

### Modules
1. If you want to import a module as a whole, you can do it using the `import module_name` statement. You are allowed to import more than one module at once using a comma-separated list. For example:
    ```python
    import mod1
    import mod2, mod3, mod4
    ```
    although the latter form is not recommended due to stylistic reasons, and it's better and prettier to express the same intention in more a verbose and explicit form, such as:
    ```python
    import mod2
    import mod3
    import mod4
    ```

2. If a module is imported in the above manner and you want to access any of its entities, you need to prefix the entity's name using **dot notation**. For example:
    ```python
    import my_module
    
    result = my_module.my_function(my_module.my_data)
    ```
    The snippet makes use of two entities coming from the `my_module` module: a function named `my_function()` and a variable named `my_data`. Both names must be prefixed by `my_module.` None of the imported entity names conflicts with the identical names existing in your code's namespace.

3. You are allowed not only to import a module as a whole, but to import only individual entities from it. In this case, the imported entities **must not be** prefixed when used. For example:
   ```python
   from module import my_function, my_data
   
   result = my_function(my_data)
   ```
   The above way - despite its attractiveness - is not recommended because of the danger of causing conflicts with names derived from importing the code's namespace.

4. The most general form of the above statement allows you to import **all entities** offered by a module:
   ```python
   from my_module import *
   
   result = my_function(my_data)
   ```
   **Note**: this import's variant is not recommended due to the same reasons as previously (the threat of a naming conflict is even more dangerous here).

5. You can change the name of the imported entity "on the fly" by using the `as` phrase of the `import`. For example:
   ```python
   from module import my_function as fun, my_data as dat
   
   result = fun(dat)
   ```

### Standard modules
1. A function named `dir()` can show you a list of the entities contained inside an imported module. For example:
   ```python
   import os
   dir(os)
   ```
   prints out the list of all the `os` module's facilities you can use in your code.

2. The `math` module couples more than 50 symbols (functions and constants) that perform mathematical operations (like `sine()`, `pow()`, `factorial()`) or providing important values (like **π** and the Euler symbol **e**).
3. The `random` module groups more than 60 entities designed to help you use pseudo-random numbers. Don't forget the prefix "random", as there is no such thing as a real random number when it comes to generating them using the computer's algorithms.
4. The `platform` module contains about 70 functions which let you dive into the underlaying layers of the OS and hardware. Using them allows you to get to know more about the environment in which your code is executed.
5. **Python Module Index** (https://docs.python.org/3/py-modindex.html is a community-driven directory of modules available in the Python universe. If you want to find a module fitting your needs, start your search there.

### Packages
1. While a **module** is designed to couple together some related entities (functions, variables, constants, etc.), a **package** is a container which enables the coupling of several related modules under one common name. Such a container can be distributed as-is (as a batch of files deployed in a directory sub-tree) or it can be packed inside a zip file.
2. During the very first import of the actual module, Python translates its source code into the **semi-compiled** format stored inside the **pyc** files, and deploys these files into the `__pycache__` directory located in the module's home directory.
3. If you want to instruct your module's user that a particular entity should be treated as **private** (i.e. not to be explicitly used outside the module) you can mark its name with either the `_` or `__` prefix. Don't forget that this is only a recommendation, not an order.
4. The names _shabang, shebang, hasbang, poundbang,_ and _hashpling_ describe the digraph written as `#!`, used to instruct Unix-like OSs how the Python source file should be launched. This convention has no effect under MS Windows.
5. If you want convince Python that it should take into account a non-standard package's directory, its name needs to be inserted/appended into/to the import directory list stored in the `path` variable contained in the `sys` module.
6. A Python file named `__init__.py` is implicitly run when a package containing it is subject to import, and is used to initialize a package and/or its sub-packages (if any). The file may be empty, but must not be absent.

### Python Package Installer (PIP)
1. A **repository** (or **repo** for short) designed to collect and share free Python code exists and works under the name **Python Package Index (PyPI)** although it's also likely that you come across a very niche name **The Cheese Shop**. The Shop's website is available at https://pypi.org/.
2. To make use of The Cheese Shop the specialized tool has been created and its name is **pip** (**p**ip **i**nstalls **p**ackages while pip stands for... ok, don't mind). As pip may not be deployed as a part of standard Python installation, it is possible that you will need to install it manually. Pip is a console tool.
3. To check pip's version one the following commands should be issued:
   ```
   pip --version
   ```
   or
   ```
   pip3 --version
   ```
   Check yourself which of these works for you in your OS' environment.
4. List of main **pip** activities looks as follows:
- `pip help operation` - shows brief pip's description;
- `pip list` - shows list of currently installed packages;
- `pip show package_name` - shows package_name info including package's dependencies;
- `pip search anystring` - searches through PyPI directories in order to find packages which name contains anystring;
- `pip install name` - installs name system-wide (expect problems when you don't have administrative rights);
- `pip install --user name` - install name for you only; no other your platform's user will be able to use it;
- `pip install -U name` - updates previously installed package;
- `pip uninstall name` - uninstalls previously installed package;