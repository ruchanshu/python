# The input() function 

The `input()` function is able to read data entered by the user and to return the same data to the running program.

The program can manipulate the data, making the code truly interactive.

Virtually all programs **read and process data**. A program which doesn't get a user's input is a **deaf program**.

Take a look at our example:
```python
print("Tell me anything...")
anything = input()
print("Hmm...", anything, "... Really?")
```
Note:
- The program **prompts the user to input some data** from the console (most likely using a keyboard, although it is also possible to input data using voice or image);
- the `input()` function is invoked without arguments (this is the simplest way of using the function); the function will **switch the console to input mode**; you'll see a blinking cursor, and you'll be able to input some keystrokes, finishing off by hitting the Enter key; all the inputted data will be **sent to your program** through the function's result;
- note: you need to assign the result to a variable; this is crucial - missing out this step will cause the entered data to be lost;
- then we use the `print()` function to output the data we get, with some additional remarks.

### The input() function with an argument
The `input()` function can do something else: it can prompt the user without any help from `print()`.

We've modified our example a bit, look at the code:
```python
anything = input("Tell me anything...")
print("Hmm...", anything, "...Really?")
```
Note:
- the `input()` function is invoked with one argument - it's a string containing a message;
- the message will be displayed on the console before the user is given an opportunity to enter anything;
- `input()` will then do its job.

### The result of the input() function
> [!WARNING]
> The result of the `input()` function is a string.

A string containing all the characters the user enters from the keyboard. It is not an integer or a float.

This means that **you mustn't use it as an argument of any arithmetic operation**, e.g., you can't use this data to square it, divide it by anything, or divide anything by it.
```python
anything = input("Enter a number: ")
something = anything ** 2.0
print(anything, "to the power of 2 is", something)
```
What happens?

Python should have given you the following output:
```
Traceback (most recent call last):
File ".main.py", line 4, in <module>
something = anything ** 2.0
TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'float'
```

The last line of the sentence explains everything - you tried to apply the `**` operator to `'str'` (string) accompanied with `'float'`.

This is prohibited.

This should be obvious - can you predict the value of `"to be or not to be"` raised to the power of `2`?

We can't. Python can't either.