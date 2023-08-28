## Summary

### Modules, Packages and PIP
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
