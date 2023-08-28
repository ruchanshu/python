# The print() function

Look at the line of code below:

```python
print("Hello, World!")
```
The word **print** that you can see here is a **function name**. That doesn't mean that wherever the word appears it is always a function name. The meaning of the word comes from the context in which the word has been used.

A function (in this context) is a separate part of the computer code able to:
- **cause some effect** (e.g., send text to the terminal, create a file, draw an image, play a sound, etc.); this is something completely unheard of in the world of mathematics;
- **evaluate a value** (e.g., the square root of a value or the length of a given text) and **return it as the function's result**; this is what makes Python functions the relatives of mathematical concepts.

Where do the functions come from?
- They may come **from Python itself**; the print function is one of this kind; such a function is an added value received together with Python and its environment (it is **built-in**)
- they may come from one or more of Python's add-ons named **modules**; some of the modules come with Python, others may require separate installation
- you can **write them yourself**, placing as many functions as you want and need inside your program to make it simpler, clearer and more elegant.

The name of the function should be **significant** (the name of the print function is self-evident).

The function name (**_print_** in this case) along with the parentheses and argument(s), forms the **function invocation**.

What happens when Python encounters an invocation like this one below?

```python
function_name(argument)
```
Let's see:
- First, Python checks if the name specified is **legal** (it browses its internal data in order to find an existing function of the name; if this search fails, Python aborts the code);
- second, Python checks if the function's requirements for the number of arguments **allows you to invoke** the function in this way (e.g., if a specific function demands exactly two arguments, any invocation delivering only one argument will be considered erroneous, and will abort the code's execution);
- third, Python **leaves your code for a moment** and jumps into the function you want to invoke; of course, it takes your argument(s) too and passes it/them to the function;
- fourth, the function **executes its code**, causes the desired effect (if any), evaluates the desired result(s) (if any) and finishes its task;
- finally, Python **returns to your code** (to the place just after the invocation) and resumes its execution.

## The print() function - using multiple arguments

**the positional way** - the argument is dictated by its position, e.g., the second argument will be outputted after the first, not the other way r

```python
print("The itsy bitsy spider" , "climbed up" , "the waterspout.")
```
There is one print() function invocation, but it contains **three arguments**. All of them are strings. The arguments are separated by commas. We've surrounded them with spaces to make them more visible, but **it's not really necessary**.

Two conclusions emerge from this example:
- a print() function invoked with more than one argument **outputs them all on one line**;
- the print() function **puts a space between the outputted arguments** on its own initiative.

**keyword arguments** - these arguments is taken not from its location (position) but from the special word (keyword) used to identify them.

In order to use it, it is necessary to know some rules:
- a keyword argument consists of three elements: a **keyword** identifying the argument (end here); an equal sign (=); and a value assigned to that argument;
- any keyword arguments have to be put **after the last positional argument** (this is very important)

```python
print("My", "name", "is", sep="_", end="*")
print("Monty", "Python.", sep="*", end="*\n")
```

The console should now be showing the following text:
```
My_name_is*Monty*Python.*
```

The default behavior reflects the situation where the end keyword argument is **implicitly** used in the following way: end="\n".