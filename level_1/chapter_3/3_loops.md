# Loops

Performing a certain part of the code more than once is called a **loop**. 

## Looping your code with while
In general, in Python, a loop can be represented as follows:
```python
while conditional_expression:
    instruction
```
If you notice some similarities to the _if_ instruction, that's quite all right. Indeed, the syntactic difference is only one: you use the word `while` instead of the word `if`.

The semantic difference is more important: when the condition is met, if performs its statements **only once**; _while_ **repeats the execution as long as the condition evaluates to `True`**.

> [!NOTE]
> All the rules regarding indentation are applicable here, too.

Look at the algorithm below:
```python
while conditional_expression:
    instruction_one
    instruction_two
    instruction_three
    :
    :
    instruction_n
```
It is now important to remember that:
- if you want to execute **more than one statement inside one `while`**, you must (as with `if`) **indent** all the instructions in the same way;
- an instruction or set of instructions executed inside the `while` loop is called the **loop's body**;
- if the condition is `False` (equal to zero) as early as when it is tested for the first time, the body is not executed even once (note the analogy of not having to do anything if there is nothing to do);
- the body should be able to change the condition's value, because if the condition is `True` at the beginning, the body might run continuously to infinity - notice that doing a thing usually decreases the number of things to do).

### An infinite loop
An infinite loop, also called an **endless loop**, is a sequence of instructions in a program which repeat indefinitely (loop endlessly.)

Here's an example of a loop that is not able to finish its execution:
```python
while True:
    print("I'm stuck inside a loop.")
```
This loop will infinitely print `I'm stuck inside a loop.` on the screen.

### Using a counter variable to exit a loop
Try to recall how Python interprets the truth of a condition, and note that these two forms are equivalent:

`while number != 0:` and `while number:`.

The condition that checks if a number is odd can be coded in these equivalent forms, too:

`if number % 2 == 1:` and `if number % 2:`.

```python
counter = 5
while counter != 0:
    print("Inside the loop.", counter)
    counter -= 1
print("Outside the loop.", counter)
```
This code is intended to print the string `"Inside the loop."` and the value stored in the `counter` variable during a given loop exactly five times. Once the condition has not been met (the `counter` variable has reached `0`), the loop is exited, and the message `"Outside the loop."` as well as the value stored in `counter` is printed.

But there's one thing that can be written more compactly - the condition of the `while` loop.

Can you see the difference?
```python
counter = 5
while counter:
    print("Inside the loop.", counter)
    counter -= 1
print("Outside the loop.", counter)
```
Is it more compact than previously? A bit. Is it more legible? That's disputable.
> Don't feel obliged to code your programs in a way that is always the shortest and the most compact. Readability may be a more important factor. Keep your code ready for a new programmer.

## Looping your code with for
Another kind of loop available in Python comes from the observation that sometimes it's more important to **count the "turns" of the loop** than to check the conditions.

Imagine that a loop's body needs to be executed exactly one hundred times. If you would like to use the `while` loop to do it, it may look like this:
```python
i = 0
while i < 100:
    # do_something()
    i += 1
```
Actually, the `for` loop is designed to do more complicated tasks - **it can "browse" large collections of data item by item**. We'll show you how to do that soon, but right now we're going to present a simpler variant of its application.

Take a look at the snippet:
```python
for i in range(100):
    # do_something()
    pass
```
There are some new elements. Let us tell you about them:
- the _for_ keyword opens the `for` loop; note - there's no condition after it; you don't have to think about conditions, as they're checked internally, without any intervention;
- any variable after the _for_ keyword is the **control variable** of the loop; it counts the loop's turns, and does it automatically;
- the _in_ keyword introduces a syntax element describing the range of possible values being assigned to the control variable;
- the `range()` function (this is a very special function) is responsible for generating all the desired values of the control variable; in our example, the function will create (we can even say that it will **feed** the loop with) subsequent values from the following set: 0, 1, 2 .. 97, 98, 99; note: in this case, the `range()` function starts its job from 0 and finishes it one step (one integer number) before the value of its argument;
- note the _pass_ keyword inside the loop body - it does nothing at all; it's an **empty instruction** - we put it here because the `for` loop's syntax demands at least one instruction inside the body (by the way - `if`, `elif`, `else` and `while` express the same thing)

## The range() function  

Take a look at the snippet below. Can you predict its output?
```python
for i in range(10):
    print("The value of i is currently", i)
```
Note:
- the loop has been executed ten times (it's the `range()` function's argument)
- the last control variable's value is `9` (not `10`, as it starts from `0`, not from `1`)

###  the range() function with two arguments
The `range()` function invocation may be equipped with two arguments, not just one:
```python
for i in range(2, 8):
    print("The value of i is currently", i)
```
In this case, the first argument determines the initial (first) value of the control variable.

The last argument shows the first value the control variable will not be assigned.

> [!IMPORTANT]
> the range() function **accepts only integers as its arguments**, and generates sequences of integers.

Can you guess the output of the program? Run it to check if you were right now, too.

The first value shown is `2` (taken from the `range()`'s first argument.)

The last is `7` (although the `range()`'s second argument is `8`).

###  the range() function with three arguments
The `range()` function may also accept `three arguments`
```python
for i in range(2, 8, 3):
    print("The value of i is currently", i)
```
The third argument is an **increment** - it's a value added to control the variable at every loop turn (as you may suspect, the **default value of the increment is 1**).

You should be able to see the following lines in the console window:
```
The value of i is currently 2
The value of i is currently 5
```
The first argument passed to the `range()` function tells us what the **starting** number of the sequence is (hence `2` in the output). The second argument tells the function where to **stop** the sequence (the function generates numbers up to the number indicated by the second argument, but does not include it). Finally, the third argument indicates the **step**, which actually means the difference between each number in the sequence of numbers generated by the function.

`2` (starting number) → `5` (`2` increment by `3` equals `5` - the number is within the range from 2 to 8) → `8` (`5` increment by `3` equals `8` - the number is not within the range from 2 to 8, because the stop parameter is not included in the sequence of numbers generated by the function.)

> [!NOTE]
> If the set generated by the `range()` function is empty, the loop won't execute its body at all.
>
>Just like here - there will be no output:
>
>```python
>for i in range(1, 1):
>    print("The value of i is currently", i)
>```


> [!NOTE]
>The set generated by the `range()` has to be sorted in **ascending order**. There's no way to force the `range()` to create a set in a different form when the `range()` function accepts exactly two arguments. This means that the `range()`'s second argument must be greater than the first.
>
>Thus, there will be no output here, either:
>```python
>for i in range(2, 1):
>    print("The value of i is currently", i)
>```

## The `break` and `continue` statements
So far, we've treated the body of the loop as an indivisible and inseparable sequence of instructions that are performed completely at every turn of the loop. However, as developer, you could be faced with the following choices:

- it appears that it's unnecessary to continue the loop as a whole; you should refrain from further execution of the loop's body and go further;
- it appears that you need to start the next turn of the loop without completing the execution of the current turn.

Python provides two special instructions for the implementation of both these tasks. Let's say for the sake of accuracy that their existence in the language is not necessary - an experienced programmer is able to code any algorithm without these instructions. Such additions, which don't improve the language's expressive power, but only simplify the developer's work, are sometimes called **syntactic candy**, or syntactic sugar.

These two instructions are:
- `break` - exits the loop immediately, and unconditionally ends the loop's operation; the program begins to execute the nearest instruction after the loop's body;
- `continue` - behaves as if the program has suddenly reached the end of the body; the next turn is started and the condition expression is tested immediately.
Both these words are **keywords**.

```python
# break - example

print("The break instruction:")
for i in range(1, 6):
    if i == 3:
        break
    print("Inside the loop.", i)
print("Outside the loop.")


# continue - example

print("\nThe continue instruction:")
for i in range(1, 6):
    if i == 3:
        continue
    print("Inside the loop.", i)
print("Outside the loop.")
```

Analyze the code, and judge whether and how you would use either of them.

The `break` variant goes here:
```python
largest_number = -99999999
counter = 0

while True:
    number = int(input("Enter a number or type -1 to end program: "))
    if number == -1:
        break
    counter += 1
    if number > largest_number:
        largest_number = number

if counter != 0:
    print("The largest number is", largest_number)
else:
    print("You haven't entered any number.")
```

And now the continue variant:
```python
largest_number = -99999999
counter = 0

number = int(input("Enter a number or type -1 to end program: "))

while number != -1:
    if number == -1:
        continue
    counter += 1

    if number > largest_number:
        largest_number = number
    number = int(input("Enter a number or type -1 to end program: "))

if counter:
    print("The largest number is", largest_number)
else:
    print("You haven't entered any number.")
```
Look carefully, the user enters the first number **before** the program enters the `while` loop. The subsequent number is entered when the program is **already in the loop**.

### The while loop and the else branch
Both loops, `while` and `for`, have one interesting (and rarely used) feature.

In other words, try to convince yourself if the feature is valuable and useful, or is just syntactic sugar.

Take a look at the snippet in the editor. There's something strange at the end - the `else` keyword.

As you may have suspected, **loops may have the `else` branch too, like `if`s**.

The `loop`'s else branch is **always executed once, regardless of whether the loop has entered its body or not**.
```python
i = 1
while i < 5:
    print(i)
    i += 1
else:
    print("else:", i)
```
Can you guess the output? Run the program to check if you were right.

Modify the snippet a bit so that the loop has no chance to execute its body even once:
```python
i = 5
while i < 5:
    print(i)
    i += 1
else:
    print("else:", i)
```
The `while`'s condition is `False` at the beginning - can you see it?

### The for loop and the else branch
`for` loops behave a bit differently.
```python
for i in range(5):
    print(i)
else:
    print("else:", i)
```
The output may be a bit surprising.

The `i` variable retains its last value.

Modify the code a bit to carry out one more experiment.
```python
i = 111
for i in range(2, 1):
    print(i)
else:
    print("else:", i)
```
The loop's body won't be executed here at all. Note: we've assigned the `i` variable before the loop.

When the loop's body isn't executed, the control variable retains the value it had before the loop.

> [!WARNING]
> If the control variable doesn't exist before the loop starts, it won't exist when the execution reaches the `else` branch.
