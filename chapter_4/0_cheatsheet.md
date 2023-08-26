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
    def your_function(optional_parameters):
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

### Functions Parameters and Argument Passing
1. You can pass information to functions by using parameters. Your functions can have as many parameters as you need.

   An example of a one-parameter function:
   ```python
   def hi(name):
       print("Hi,", name)
   
   hi("Greg")
   ```
   An example of a two-parameter function:
   ```python
   def hi_all(name_1, name_2):
       print("Hi,", name_2)
       print("Hi,", name_1)
   
   hi_all("Sebastian", "Konrad")
   ```
   An example of a three-parameter function:
   ```python
   def address(street, city, postal_code):
       print("Your address is:", street, "St.,", city, postal_code)
   
   s = input("Street: ")
   p_c = input("Postal Code: ")
   c = input("City: ")
   
   address(s, c, p_c)
   ```
2. You can pass arguments to a function using the following techniques:
   - **positional argument passing** in which the order of arguments passed matters (Ex. 1),
   - **keyword (named) argument passing** in which the order of arguments passed doesn't matter (Ex. 2),
   - a mix of positional and keyword argument passing (Ex. 3).
   ```python
   Ex. 1
   def subtra(a, b):
       print(a - b)
   
   subtra(5, 2)    # outputs: 3
   subtra(2, 5)    # outputs: -3
   
   
   Ex. 2
   def subtra(a, b):
       print(a - b)
   
   subtra(a=5, b=2)    # outputs: 3
   subtra(b=2, a=5)    # outputs: 3
   
   Ex. 3
   def subtra(a, b):
       print(a - b)
   
   subtra(5, b=2)    # outputs: 3
   subtra(5, 2)    # outputs: 3
   ```
   It's important to remember that **positional arguments mustn't follow keyword arguments**. That's why if you try to run the following snippet:
   ```python
   def subtra(a, b):
       print(a - b)
   
   subtra(5, b=2)    # outputs: 3
   subtra(a=5, 2)    # Syntax Error
   ```
   
   Python will not let you do it by signalling a `SyntaxError`.
3. You can use the keyword argument passing technique to **pre-define** a value for a given argument:
   ```python
   def name(first_name, last_name="Smith"):
       print(first_name, last_name)
   
   name("Andy")    # outputs: Andy Smith
   name("Betty", "Johnson")    # outputs: Betty Johnson (the keyword argument replaced by "Johnson")
   ```
   
### Functions `return` instruction
1. You can use the `return` keyword to tell a function to return some value. The `return` statement exits the function, e.g.:
   ```python
   def multiply(a, b):
       return a * b
   
   print(multiply(3, 4))    # outputs: 12
   
   
   def multiply(a, b):
       return
   
   print(multiply(3, 4))    # outputs: None
   ```
2. The result of a function can be easily assigned to a variable, e.g.:
   ```python
   def wishes():
       return "Happy Birthday!"
   
   w = wishes()
   
   print(w)    # outputs: Happy Birthday!
   ```
   Look at the difference in output in the following two examples:
   ```python
   # Example 1
   def wishes():
       print("My Wishes")
       return "Happy Birthday"
   
   wishes()    # outputs: My Wishes
   
   
   # Example 2
   def wishes():
       print("My Wishes")
       return "Happy Birthday"
   
   print(wishes())
   
   # outputs: My Wishes
   #          Happy Birthday
   ```
3. You can use a list as a function's argument, e.g.:
   ```python
   def hi_everybody(my_list):
       for name in my_list:
           print("Hi,", name)
   
   hi_everybody(["Adam", "John", "Lucy"])
   ```
4. A list can be a function result, too, e.g.:
   ```python
   def create_list(n):
       my_list = []
       for i in range(n):
           my_list.append(i)
       return my_list
   
   print(create_list(5))
   ```
