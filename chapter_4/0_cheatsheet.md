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

### Functions and Scopes
1. A variable that exists outside a function has a scope inside the function body (Example 1) unless the function defines a variable of the same name (Example 2, and Example 3), e.g.:
   
   Example 1:

   ```python
   var = 2
   
   
   def mult_by_var(x):
       return x * var
   
   
   print(mult_by_var(7))    # outputs: 14
   ```
   Example 2:
   ```python
   def mult(x):
       var = 5
       return x * var
   
   
   print(mult(7))    # outputs: 35
   ```
   Example 3:
   ```python
   def mult(x):
       var = 7
       return x * var
   
   
   var = 3
   print(mult(7))    # outputs: 49
   ```
2. A variable that exists inside a function has a scope inside the function body (Example 4), e.g.:

   Example 4:
   ```python
   def adding(x):
       var = 7
       return x + var
   
   
   print(adding(4))    # outputs: 11
   print(var)    # NameError
   ```
3. You can use the `global` keyword followed by a variable name to make the variable's scope global, e.g.:
   ```python
   var = 2
   print(var)    # outputs: 2
   
   
   def return_var():
       global var
       var = 5
       return var
   
   
   print(return_var())    # outputs: 5
   print(var)    # outputs: 5
   ```

### Recursion
1. A function can call other functions or even itself. When a function calls itself, this situation is known as **recursion**, and the function which calls itself and contains a specified termination condition (i.e., the base case - a condition which doesn't tell the function to make any further calls to that function) is called a **recursive function**.
2. You can use recursive functions in Python to write **clean, elegant code, and divide it into smaller, organized chunks**. On the other hand, you need to be very careful as it might be **easy to make a mistake and create a function which never terminates**. You also need to remember that **recursive calls consume a lot of memory**, and therefore may sometimes be inefficient.
   - When using recursion, you need to take all its advantages and disadvantages into consideration.
   - The factorial function is a classic example of how the concept of recursion can be put in practice:
   ```python
   # Recursive implementation of the factorial function.
   
   def factorial(n):
       if n == 1:    # The base case (termination condition.)
           return 1
       else:
           return n * factorial(n - 1)
   
   
   print(factorial(4)) # 4 * 3 * 2 * 1 = 24
   ```