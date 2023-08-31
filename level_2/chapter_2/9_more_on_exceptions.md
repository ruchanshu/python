# More on Exceptions

## Errors, failures, and other plagues
#### Anything that can go wrong, will go wrong.
This is Murphy's law, and it works everywhere and always. Your code's execution can go wrong, too. If it can, it will.
```python
import math

x = float(input("Enter x: "))
y = math.sqrt(x)

print("The square root of", x, "equals to", y)
```
Look the code in the editor. There are at least two possible ways it can "go wrong". Can you see them?
- As a user is able to enter a completely arbitrary string of characters, **there is no guarantee that the string can be converted into a float value** - this is the first vulnerability of the code;
- the second is that the `sqrt()` **function fails if it gets a negative argument.**

You may get one of the following error messages.

Something like this:
```
Enter x: Abracadabra

Traceback (most recent call last):

  File "sqrt.py", line 3, in <module>

    x = float(input("Enter x: "))

ValueError: could not convert string to float: 'Abracadabra'
```
Or something like this:
```
Enter x: -1

Traceback (most recent call last):

  File "sqrt.py", line 4, in <module>

    y = math.sqrt(x)

ValueError: math domain error
```
Can you protect yourself from such surprises? Of course you can. Moreover, you have to do it in order to be considered a good programmer.

## Exceptions
Each time your code tries to do something wrong/foolish/irresponsible/crazy/unenforceable, Python does two things:
- it **stops your program**;
- it creates a special kind of data, called an **exception**.

Both of these activities are called **raising an exception**. We can say that Python always raises an exception (or that an **exception has been raised**) when it has no idea what to do with your code.

Python provides effective tools that allow you to **observe exceptions, identify them and handle them** efficiently. This is possible due to the fact that all potential exceptions have their unambiguous names, so you can categorize them and react appropriately.

You know some exception names already. Take a look at the following diagnostic message:
```
ValueError: math domain error
```
The word highlighted above is just the **exception name**. Let's get familiar with some other exceptions

```python
value = 1
value /= 0
```
Run the (obviously incorrect) program.

You will see the following message in reply:
```
Traceback (most recent call last):
File "div.py", line 2, in 
value /= 0
ZeroDivisionError: division by zero
```
This exception error is called `ZeroDivisionError`.

```python
my_list = []
x = my_list[0]
```
What will happen when you run it? Check.

You will see the following message in reply:
```python
Traceback (most recent call last):
File "lst.py", line 2, in 
x = list[0]
IndexError: list index out of range
```
This is the `IndexError`.

### How do you handle exceptions? 
The word `try` is key to the solution.

What's more, it's a keyword, too.

The recipe for success is as follows:
- first, you have to **_try_ to do something**;
- next, you have to **check whether everything went well**.

But wouldn't it be better to check all circumstances first and then do something only if it's safe?
```python
first_number = int(input("Enter the first number: "))
second_number = int(input("Enter the second number: "))

if second_number != 0:
    print(first_number / second_number)
else:
    print("This operation cannot be done.")

print("THE END.")
```
Admittedly, this way may seem to be the most natural and understandable, but in reality, this method doesn't make programming any easier. All these checks can make **your code bloated and illegible**.

Python prefers a completely different approach.
```python
first_number = int(input("Enter the first number: "))
second_number = int(input("Enter the second number: "))

try:
    print(first_number / second_number)
except:
    print("This operation cannot be done.")

print("THE END.")
```
Note:
- the `try` keyword **begins a block of the code** which may or may not be performing correctly;
- next, Python tries to perform the risky action; if it fails, an exception is raised and Python starts to look for a solution;
- the `except` keyword starts a piece of code which will be **executed if anything inside the `try` block goes wrong** - if an exception is raised inside a previous `try` block, **it will fail here**, so the code located after the except keyword should provide an **adequate reaction** to the raised exception;
- returning to the previous nesting level ends the **try-except** section.

Run the code and test its behavior.

Let's summarize this:
```python
try:
    :
    :
except:
    :
    :
```
- in the first step, Python tries to perform all instructions placed between the `try:` and `except:` statements;
- if nothing is wrong with the execution and all instructions are performed successfully, the execution jumps to the point after the last line of the `except:` block, and the block's execution is considered complete;
- if anything goes wrong inside the `try:` and `except:` block, the execution immediately jumps out of the block and into the first instruction located after the except: keyword; this means that some of the instructions from the block may be silently omitted.

Look at the code. It will help you understand this mechanism.
```python
try:
    print("1")
    x = 1 / 0
    print("2")
except:
    print("Oh dear, something went wrong...")

print("3")
```
This is the output it produces:
```
1
Oh dear, something went wrong...
3
```

> [!NOTE]
> The `print("2")` instruction was lost in the process.

This approach has one important disadvantage - if there is a possibility that more than one exception may skip into an `except:` branch, you may have **trouble figuring out what actually happened**.

Just like in our code in the editor. Run it and see what happens.
```python
try:
    x = int(input("Enter a number: "))
    y = 1 / x
except:
    print("Oh dear, something went wrong...")

print("THE END.")
```
The message: `Oh dear, something went wrong...` appearing in the console says nothing about the reason, while there are two possible causes of the exception:
- non-integer data entered by the user;
- an integer value equal to `0` assigned to the `x` variable.

Technically, there are two ways to solve the issue:
- build two consecutive try-except blocks, one for each possible exception reason (easy, but will cause unfavorable code growth)
- use a more advanced variant of the instruction.

It looks like this:
```python
try:
    :
except exc1:
    :
except exc2:
    :
except:
    :
```
This is how it works:
- if the `try` branch raises the `exc1` exception, it will be handled by the `except exc1:` block;
- similarly, if the `try` branch raises the `exc2` exception, it will be handled by the `except exc2:` block;
- if the `try` branch raises any other exception, it will be handled by the unnamed `except` block.

```python
try:
    x = int(input("Enter a number: "))
    y = 1 / x
    print(y)
except ZeroDivisionError:
    print("You cannot divide by zero, sorry.")
except ValueError:
    print("You must enter an integer value.")
except:
    print("Oh dear, something went wrong...")

print("THE END.")
```
The code, when run, produces one of the following four variants of output:
- if you enter a valid, non-zero integer value (e.g., `5`) it says:
    ```
    0.2
    THE END.
    ```
- if you enter `0`, it says:
    ```
    You cannot divide by zero, sorry.
    THE END.
    ```
- if you enter any non-integer string, you see:
    ```
    You must enter an integer value.
    THE END.
    ```
- (locally on your machine) if you press Ctrl-C while the program is waiting for the user's input (which causes an exception named `KeyboardInterrupt`), the program says:
    ```
    Oh dear, something went wrong...
    THE END.
    ```

Don't forget that:
- the `except` branches are searched in the same order in which they appear in the code;
- you must not use more than one except branch with a certain exception name;
- the number of different `except` branches is arbitrary - the only condition is that if you use `try`, you must put at least one `except` (named or not) after it;
- the `except` keyword must not be used without a preceding `try`;
- if any of the `except` branches is executed, no other branches will be visited;
- if none of the specified `except` branches matches the raised exception, the exception remains unhandled (we'll discuss it soon)
- if an unnamed `except` branch exists (one without an exception name), it has to be specified as the last.
```python
try:
    :
except exc1:
    :
except exc2:
    :
except:
    :
```
Let's continue the experiments now.

Look at the code in the editor. We've modified the previous program - we've removed the `ZeroDivisionError` branch.
```python
try:
    x = int(input("Enter a number: "))
    y = 1 / x
    print(y)
except ValueError:
    print("You must enter an integer value.")
except:
    print("Oh dear, something went wrong...")

print("THE END.")
```
What happens now if the user enters `0` as an input?

As there are **no dedicated branches** for division by zero, the raised exception falls into the **general (unnamed) branch**; this means that in this case, the program will say:
```
Oh dear, something went wrong...
THE END.
```
Let's spoil the code once again.

Look at the program in the editor. This time, we've removed the unnamed branch.
```python
try:
    x = int(input("Enter a number: "))
    y = 1 / x
    print(y)
except ValueError:
    print("You must enter an integer value.")

print("THE END.")
```
The user enters `0` once again and:
- the exception raised won't be handled by `ValueError` - it has nothing to do with it;
- as there's no other branch, you should to see this message:
  ```
  Traceback (most recent call last):
  File "exc.py", line 3, in 
  y = 1 / x
  ZeroDivisionError: division by zero
  ```

# Exception Hierarchy
Python 3 defines **63 built-in exceptions**, and all of them form a **tree-shaped hierarchy**, although the tree is a bit weird as its root is located on top.

Some of the built-in exceptions are more general (they include other exceptions) while others are completely concrete (they represent themselves only). We can say that **the closer to the root an exception is located, the more general (abstract) it is**. In turn, the exceptions located at the branches' ends (we can call them leaves) are concrete.

Take a look at the figure:

<p align="center">
  <img src="images/packages/exception_hierarchy.png">
</p>

It shows a small section of the complete exception tree. Let's begin examining the tree from the `ZeroDivisionError` leaf.

Note:
- `ZeroDivisionError` is a special case of more a general exception class named `ArithmeticError`;
- `ArithmeticError` is a special case of a more general exception class named just `Exception`;
- `Exception` is a special case of a more general class named `BaseException`;

Look at the code in the editor. It is a simple example to start with. Run it.
```python
try:
    y = 1 / 0
except ZeroDivisionError:
    print("Oooppsss...")

print("THE END.")
```
The output we expect to see looks like this:
```
Oooppsss...
THE END.
```
Now look at the code below:
```python
try:
    y = 1 / 0
except ArithmeticError:
    print("Oooppsss...")

print("THE END.")
```
Something has changed in it - we've replaced `ZeroDivisionError` with `ArithmeticError`.

You already know that `ArithmeticError` is a general class including (among others) the `ZeroDivisionError` exception.

Thus, the code's output remains unchanged. Test it.

This also means that replacing the exception's name with either `Exception` or `BaseException` won't change the program's behavior.

Let's summarize:
- each exception raised **falls into the first matching branch**;
- the matching branch doesn't have to specify the same exception exactly - it's enough that the exception is **more general** (more abstract) than the raised one.

Look at the code in the editor. What will happen here?
```python
try:
    y = 1 / 0
except ZeroDivisionError:
    print("Zero Division!")
except ArithmeticError:
    print("Arithmetic problem!")

print("THE END.")
```
The first matching branch is the one containing `ZeroDivisionError`. It means that the console will show:
```
Zero division!
THE END.
```
Will it change anything if we swap the two `except` branches around? Just like here below:
```python
try:
    y = 1 / 0
except ArithmeticError:
    print("Arithmetic problem!")
except ZeroDivisionError:
    print("Zero Division!")

print("THE END.")
```
The change is radical - the code's output is now:
```
Arithmetic problem!
THE END.
```
Why, if the exception raised is the same as previously?

The exception is the same, but the more general exception is now listed first - it will catch all zero divisions too. It also means that there's no chance that any exception hits the `ZeroDivisionError` branch. This branch is now completely unreachable.

Remember:
- the order of the branches matters!
- don't put more general exceptions before more concrete ones;
- this will make the latter one unreachable and useless;
- moreover, it will make your code messy and inconsistent;
- Python won't generate any error messages regarding this issue.

If you want to **handle two or more exceptions** in the same way, you can use the following syntax:
```python
try:
    :
except (exc1, exc2):
    :
```
You simply have to put all the engaged exception names into a comma-separated list and not to forget the parentheses.

If an **exception is raised inside a function**, it can be handled:
- inside the function;
- outside the function;

Let's start with the first variant - look at the code in the editor.
```python
def bad_fun(n):
    try:
        return 1 / n
    except ArithmeticError:
        print("Arithmetic Problem!")
    return None

bad_fun(0)

print("THE END.")
```
The `ZeroDivisionError` exception (being a concrete case of the `ArithmeticError` exception class) is raised inside the `bad_fun()` function, and it doesn't leave the function - the function itself takes care of it.

The program outputs:
```
Arithmetic problem!
THE END.
```
It's also possible to let the exception propagate **outside the function**. Let's test it now.

Look at the code below:
```python
def bad_fun(n):
    return 1 / n

try:
    bad_fun(0)
except ArithmeticError:
    print("What happened? An exception was raised!")

print("THE END.")
```
The problem has to be solved by the invoker (or by the invoker's invoker, and so on).

The program outputs:
```
What happened? An exception was raised!
THE END.
```

> [!NOTE]
> The **exception raised can cross function and module boundaries**, and travel through the invocation chain looking for a matching `except` clause able to handle it.
>
> If there is no such clause, the exception remains unhandled, and Python solves the problem in its standard way - **by terminating your code and emitting a diagnostic message**.

Now we're going to suspend this discussion, as we want to introduce you to a brand new Python instruction.

### The `raise` keyword
The `raise` instruction raises the specified exception named `exc` as if it was raised in a normal (natural) way:
```python
raise exc
```
**Note:** `raise` is a keyword.

The instruction enables you to:
- **simulate raising actual exceptions** (e.g., to test your handling strategy)
- partially **handle an exception** and make another part of the code responsible for completing the handling (separation of concerns).

Look at the code. This is how you can use it in practice.
```python
def bad_fun(n):
    raise ZeroDivisionError


try:
    bad_fun(0)
except ArithmeticError:
    print("What happened? An error?")

print("THE END.")
```
The program's output remains unchanged.

In this way, you can **test your exception handling routine** without forcing the code to do stupid things

The `raise` instruction may also be utilized in the following way (note the absence of the exception's name):
```python
raise
```
There is one serious restriction: this kind of `raise` instruction may be used **inside the `except` branch only**; using it in any other context causes an error.

The instruction will immediately re-raise the same exception as currently handled.

Thanks to this, you can distribute the exception handling among different parts of the code.

Look at the code. Run it - we'll see it in action.
```python
def bad_fun(n):
    try:
        return n / 0
    except:
        print("I did it again!")
        raise


try:
    bad_fun(0)
except ArithmeticError:
    print("I see!")

print("THE END.")
```
The `ZeroDivisionError` is raised twice:
- first, inside the `try` part of the code (this is caused by actual zero division)
- second, inside the `except` part by the raise instruction.

In effect, the code outputs:
```
I did it again!
I see!
THE END.
```

### The `assert` keyword
Now is a good moment to show you another Python instruction, named `assert`. This is a keyword.
```python
assert expression
```
How does it work?
- It evaluates the expression;
- if the expression evaluates to `True`, or a non-zero numerical value, or a non-empty string, or any other value different than `None`, it won't do anything else;
- otherwise, it automatically and immediately raises an exception named `AssertionError` (in this case, we say that the assertion has failed)

How it can be used?
- you may want to put it into your code where you want to be **absolutely safe from evidently wrong data**, and where you aren't absolutely sure that the data has been carefully examined before (e.g., inside a function used by someone else)
- raising an `AssertionError` exception secures your code from producing invalid results, and clearly shows the nature of the failure;
- **assertions don't supersede exceptions or validate the data** - they are their supplements.

If exceptions and data validation are like careful driving, assertion can play the role of an airbag.

Let's see the `assert` instruction in action. Look at the code. Run it.
```python
import math

x = float(input("Enter a number: "))
assert x >= 0.0

x = math.sqrt(x)

print(x)
```
The program runs flawlessly if you enter a valid numerical value greater than or equal to zero; otherwise, it stops and emits the following message:
```
Traceback (most recent call last):
  File ".main.py", line 4, in 
    assert x >= 0.0
AssertionError
```

**Which of the exceptions will be raised through the following unsuccessful evaluation?**
```python
huge_value = 1E250 ** 2
```

## Built-in exceptions
Exceptions are as routine and normal as any other aspect of a programmer's life.

For each exception, we'll show you:
- its name;
- its location in the exception tree;
- a short description;
- a concise snippet of code showing the circumstances in which the exception may be raised.

There are lots of other exceptions to explore.

### ArithmeticError
**Location**: `BaseException` ← `Exception` ← `ArithmeticError`

**Description**: an abstract exception including all exceptions caused by arithmetic operations like zero division or an argument's invalid domain

### AssertionError
**Location**: `BaseException` ← `Exception` ← `AssertionError`

**Description**: a concrete exception raised by the assert instruction when its argument evaluates to False, None, 0, or an empty string

**Code**:
```python
from math import tan, radians
angle = int(input('Enter integral angle in degrees: '))

# We must be sure that angle != 90 + k * 180
assert angle % 180 != 90
print(tan(radians(angle)))
```

### BaseException
**Location**: `BaseException`

**Description**: the most general (abstract) of all Python exceptions - all other exceptions are included in this one; it can be said that the following two except branches are equivalent: `except:` and `except BaseException:`.

### IndexError
**Location**: `BaseException` ← `Exception` ← `LookupError` ← `IndexError`

**Description**: a concrete exception raised when you try to access a non-existent sequence's element (e.g., a list's element)

**Code**:
```python
# The code shows an extravagant way
# of leaving the loop.

the_list = [1, 2, 3, 4, 5]
ix = 0
do_it = True

while do_it:
    try:
        print(the_list[ix])
        ix += 1
    except IndexError:
        do_it = False

print('Done')
```

### KeyboardInterrupt
**Location**: `BaseException` ← `KeyboardInterrupt`

**Description**: a concrete exception raised when the user uses a keyboard shortcut designed to terminate a program's execution (Ctrl-C in most OSs); if handling this exception doesn't lead to program termination, the program continues its execution.

**Note**: this exception is not derived from the `Exception` class. Run the program in IDLE.

**Code**:
```python
# This code cannot be terminated
# by pressing Ctrl-C.

from time import sleep

seconds = 0

while True:
    try:
        print(seconds)
        seconds += 1
        sleep(1)
    except KeyboardInterrupt:
        print("Don't do that!")
```

### LookupError
**Location**: `BaseException` ← `Exception` ← `LookupError`

**Description**: an abstract exception including all exceptions caused by errors resulting from invalid references to different collections (lists, dictionaries, tuples, etc.)

### MemoryError
**Location**: `BaseException` ← `Exception` ← `MemoryError`

**Description**: a concrete exception raised when an operation cannot be completed due to a lack of free memory.

**Code**:
```python
# This code causes the MemoryError exception.
# Warning: executing this code may affect your OS.
# Don't run it in production environments!

string = 'x'
try:
    while True:
        string = string + string
        print(len(string))
except MemoryError:
    print('This is not funny!')
```

### OverflowError
**Location**: `BaseException` ← `Exception` ← `ArithmeticError` ← `OverflowError`

**Description**: a concrete exception raised when an operation produces a number too big to be successfully stored

**Code**:
```python
# The code prints subsequent
# values of exp(k), k = 1, 2, 4, 8, 16, ...

from math import exp

ex = 1

try:
    while True:
        print(exp(ex))
        ex *= 2
except OverflowError:
    print('The number is too big.')
```

### ImportError
**Location**: `BaseException` ← `Exception` ← `StandardError` ← `ImportError`

**Description**: a concrete exception raised when an import operation fails

**Code**:
```python
# One of these imports will fail - which one?

try:
    import math
    import time
    import abracadabra

except:
    print('One of your imports has failed.')
```

### KeyError
**Location**: `BaseException` ← `Exception` ← `LookupError` ← `KeyError`

**Description**: a concrete exception raised when you try to access a collection's non-existent element (e.g., a dictionary's element)

**Code**:
```python
# How to abuse the dictionary
# and how to deal with it?

dictionary = { 'a': 'b', 'b': 'c', 'c': 'd' }
ch = 'a'

try:
    while True:
        ch = dictionary[ch]
        print(ch)
except KeyError:
    print('No such key:', ch)
```
Exceptions are in fact objects - however, we can tell you nothing about this aspect until we present you with classes, objects, and the like.

For the time being, if you'd like to learn more about exceptions on your own, you look into Standard Python Library at https://docs.python.org/3.6/library/exceptions.html.
