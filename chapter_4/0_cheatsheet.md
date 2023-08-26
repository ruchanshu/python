## Summary

### Functions
1. A **function** is a block of code that performs a specific task when the function is called (invoked). You can use functions to make your code reusable, better organized, and more readable. Functions can have parameters and return values.
2. There are at least four basic types of functions in Python:
   - built-in functions which are an integral part of Python (such as the `print()` function). You can see a complete list of Python built-in functions at https://docs.python.org/3/library/functions.html.
   - the ones that come from **pre-installed modules**
   - **user-defined functions** which are written by users for users - you can write your own functions and use them freely in your code,
   - the `lambda` functions
3. You can define your own function using the def keyword and the following syntax:
    ```python
    def your_function(optional parameters):
        # the body of the function
    ```
    You can define a function which doesn't take any arguments, e.g.:
    ```python
    def message():    # defining a function
        print("Hello")    # body of the function
    
    message()    # calling the function
    ```
    You can define a function which takes arguments, too, just like the one-parameter function below:
    ```python
    def hello(name):    # defining a function
        print("Hello,", name)    # body of the function
    
    
    name = input("Enter your name: ")
    
    hello(name)    # calling the function
    ```