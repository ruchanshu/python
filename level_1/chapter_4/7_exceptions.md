# Exceptions

### Errors in data vs. errors in code
Dealing with programming errors has (at least) two sides. 
1. The one appears when you get into trouble because your – apparently correct – code is fed with bad data. For example, you expect the code will input an integer value, but your careless user enters some random letters instead.
    -   It may happen that your code will be terminated then, and the user will be left alone with a terse and ambiguous error message on the screen. The user will be unsatisfied, and you should be unsatisfied, too.
2. The other side of dealing with programming errors reveals itself when undesirable code behavior is caused by mistakes you made when you were writing your program. This kind of error is commonly called a “bug”, which is a manifestation of a well-established belief that if a program works badly, it must be caused by malicious bugs which live inside the computer hardware and cause short circuits or other interference.

### When data is not what it should be
Let's write a piece of extremely trivial code – it will read a natural number (a non-negative integer) and print its reciprocal. In this way, `2` will turn into `0.5` (1/2) and `4` into `0.25` (1/4). Here’s the program:
```python
value = int(input('Enter a natural number: '))
print('The reciprocal of', value, 'is', 1/value)
```
It seems that you already know where we are going. Yes, you're right – entering data that is not an integer (which also includes entering nothing at all) will completely ruin the program execution. This is what the code's user will see:
```
Traceback (most recent call last):
  File "code.py", line 1, in 
    value = int(input('Enter a natural number: '))
ValueError: invalid literal for int() with base 10: ''
```
All the lines Python shows you are meaningful and important, but the last line seems to be the most valuable. The first word in the line is the name of the **exception** which causes your code to stop. It's `ValueError` here. The rest of the line is just a brief explanation which more precisely specifies the cause of the occurred exception.

## The _try-except_ branch
In the Python world, there is a rule that says: _"It’s better to beg for forgiveness than to ask for permission"_.

Let's stop here for a moment. Don't get us wrong – we don't want you to apply the rule in your everyday life. Don't take anyone's car without permission in the hope that you can be so convincing that you will avoid conviction. The rule is about something else.

Actually, the rule reads: _"it's better to handle an error when it happens than to try to avoid it"_.

"Okay," you may say now, 'but how should I beg for forgiveness when the program is terminated and there is nothing left that can be done?" This is where the **exception** comes on the scene.
```python
try:
	# It's a place where
	# you can do something 
    # without asking for permission.
except:
	# It's a spot dedicated to 
    # solemnly begging for forgiveness.
```
You can see two branches here:
- first, starting with the `try` keyword – this is the place where you put the code you suspect is risky and may be terminated in case of error; note: this kind of error is called an **exception**, while the exception occurrence is called raising – we can say that an exception is (or was) raised;
- second, the part of the code starting with the `except` keyword is designed to handle the exception; it's up to you what you want to do here: you can clean up the mess or you can just sweep the problem under the carpet (although we would prefer the first solution).

So, we could say that these two blocks work like this:
- the `try` keyword marks the place where you try to do something without permission;
- the `except` keyword starts a location where you can show off your apology talents.

As you can see, this approach accepts errors (treats them as a normal part of the program's life) instead of escalating efforts to avoid errors at all.

### The exception proves the rule
Let's rewrite the code to adopt the Python approach to life:
```python
try:
    value = int(input('Enter a natural number: '))
    print('The reciprocal of', value, 'is', 1/value)        
except:
    print('I do not know what to do.')
```
Let us summarize what we talked about:
- any part of the code placed between `try` and `except` is executed in a very special way – any error which occurs here **won't terminate program execution**. Instead, the control will immediately jump to the first line situated after the `except` keyword, and no other part of the `try` branch is executed;
- the code in the `except` branch is activated only when an exception has been encountered inside the `try` block. There is no way to get there by any other means;
- when either the `try` block or the `except` block is executed successfully, the control returns to the normal path of execution, and any code located beyond in the source file is executed as if nothing happened.

Now we want to ask you an innocent question: is `ValueError` the only way the control could fall into the `except` branch?

### How to deal with more than one exception
The answer is obviously "no" – there is more than one possible way to raise an exception.

#### Two exceptions after one try
```python
try:
    value = int(input('Enter a natural number: '))
    print('The reciprocal of', value, 'is', 1/value)        
except ValueError:
    print('I do not know what to do.')    
except ZeroDivisionError:
    print('Division by zero is not allowed in our Universe.')
```
As you can see, we've just introduced the second `except` branch. This is not the only difference – note that both branches have exception **names** specified. In this variant, each of the expected exceptions has its own way of handling the error, but it must be emphasized that **only one** of all branches can intercept the control – **if one of the branches is executed, all the other branches remain idle**.

Additionally, the number of except branches is not limited – you can specify as many or as few of them as you need, but don't forget that none of the exceptions can be specified more than once.

### The default exception and how to use it
```python
try:
    value = int(input('Enter a natural number: '))
    print('The reciprocal of', value, 'is', 1/value)        
except ValueError:
    print('I do not know what to do.')    
except ZeroDivisionError:
    print('Division by zero is not allowed in our Universe.')    
except:
    print('Something strange has happened here... Sorry!')
```
The code has changed again – can you see the difference?

We've added a third `except` branch, but this time it **has no exception name specified** – we can say it's **anonymous** or (what is closer to its actual role) it's the **default**. You can expect that when an exception is raised and there is no `except` branch dedicated to this exception, it will be handled by the default branch.

> [!IMPORTANT] 
> The default except branch must be the last except branch. Always!

### Some useful exceptions
Let’s discuss in more detail some useful (or rather, the most common) exceptions you may experience.

#### ZeroDivisionError
This appears when you try to force Python to perform any operation which provokes division in which the divider is zero, or is indistinguishable from zero. Note that there is more than one Python operator which may cause this exception to raise. Can you guess them all?

Yes, they are: `/`, `//`, and `%`.

#### ValueError
Expect this exception when you're dealing with values which may be inappropriately used in some context. In general, this exception is raised when a function (like `int()` or `float()`) receives an argument of a proper type, but its value is unacceptable.

#### TypeError
This exception shows up when you try to apply a data whose type cannot be accepted in the current context. Look at the example:
```python
short_list = [1]
one_value = short_list[0.5]
```
You're not allowed to use a float value as a list index (the same rule applies to tuples, too). `TypeError` is an adequate name to describe the problem, and an adequate exception to raise.

#### AttributeError
This exception arrives – among other occasions – when you try to activate a method which doesn't exist in an item you're dealing with. For example:
```python
short_list = [1]
short_list.append(2)
short_list.depend(3)
```
The third line of our example attempts to make use of a method which isn’t contained in the lists. This is the place where `AttributeError` is raised.

#### SyntaxError
This exception is raised when the control reaches a line of code which violates Python's grammar. It may sound strange, but some errors of this kind cannot be identified without first running the code. This kind of behavior is typical of interpreted languages – the interpreter always works in a hurry and has no time to scan the whole source code. It is content with checking the code which is currently being run. An example of such a category of issues will be presented very soon.

It's a bad idea to handle this exception in your programs. You should produce code that is free of syntax errors, instead of masking the faults you’ve caused.

# Testing and Debugging

### When Python closes its eyes
```python
temperature = float(input('Enter current temperature:'))

if temperature > 0:
    print("Above zero")
elif temperature < 0:
    prin("Below zero")
else:
    print("Zero")
```
We intentionally introduced an error into the code – we hope your watchful eyes noticed it immediately. Yes, we removed just one letter and in effect, the valid `print()` function invocation turns into the obviously invalid clause "`prin()`". There is no such function as "`prin()`" in our program's scope, but is it really obvious for Python?

Run the code and enter `0`.

As you can see, the code finishes its execution without any obstacles.

How is that possible? Why does Python **overlook** such an evident developer mistake?

The answer is simpler than you may expect, and a bit disappointing, too. Python – as you know for sure – is an **interpreted language**.

### Bug vs. debug
The basic measure a developer can use against bugs is – unsurprisingly – a **debugger**, while the process during which bugs are removed from the code is called **debugging**.

A debugger is a specialized piece of software that can control how your program is executed. Using the debugger, you can execute your code line-by-line, inspect all the variables' states and change their values on demand without modifying the source code, stop program execution when certain conditions are or aren't met, and do lots of other useful tasks.

### print debugging
This form of debugging, which can be applied to your code using any kind of debugger, is sometimes called **interactive debugging**. The meaning of the term is self-explanatory – the process needs your (the developer's) interaction to be performed.

You may use one of the simplest and the oldest (but still useful) debugging tactics known as **print debugging**. The name speaks for itself – you just insert several additional `print()` invocations inside your code to output data which illustrates the path your code is currently negotiating. You can output the values of the variables which may affect the execution.