# Lists

### Why do we need lists?
It may happen that you have to read, store, process, and finally, print dozens, maybe hundreds, perhaps even thousands of numbers. What then? Do you need to create a separate variable for each value? Will you have to spend long hours writing statements like the one below?

```python
var1 = int(input())
var2 = int(input())
var3 = int(input())
var4 = int(input())
var5 = int(input())
var6 = int(input())
:
:
```
So far, you've learned how to declare variables that are able to store exactly one given value at a time. Such variables are sometimes called **scalars** by analogy with mathematics. All the variables you've used so far are actually scalars.

Think of how convenient it would be to declare a variable that could **store more than one value**.

_What if you could just number them? And then say: give me the value number 2; assign the value number 15; increase the value number 10000._

Let's create a **multi-value variable** called `numbers`; it's assigned with not just one number, but is filled with a list consisting of five values (note: the **list starts with an open square bracket and ends with a closed square bracket**; the space between the brackets is filled with five numbers separated by commas).
```python
numbers = [10, 5, 7, 2, 1]
```
Let's say the same thing using adequate terminology: **`numbers` is a list consisting of five values, all of them numbers**. We can also say that this statement creates a list of length equal to five (as in there are five elements inside it).

The elements inside a **list may have different types**. Some of them may be integers, others floats, and yet others may be lists.

Python has adopted a convention stating that the elements in a list are **always numbered starting from zero**. This means that the item stored at the beginning of the list will have the number zero. Since there are five elements in our list, the last of them is assigned the number four. Don't forget this.

Before we go any further in our discussion, we have to state the following: **our list is a collection of elements, but each element is a scalar**.

### Indexing lists
How do you change the value of a chosen element in the list?

Let's **assign a new value of `111` to the first element** in the list. We do it this way:
```python
numbers = [10, 5, 7, 2, 1]
print("Original list content:", numbers)  # Printing original list content.

numbers[0] = 111
print("New list content: ", numbers)  # Current list content.
```
And now we want **the value of the fifth element to be copied to the second element** - can you guess how to do it?
```python
numbers = [10, 5, 7, 2, 1]
print("Original list content:", numbers)  # Printing original list content.

numbers[0] = 111
print("\nPrevious list content:", numbers)  # Printing previous list content.

numbers[1] = numbers[4]  # Copying value of the fifth element to the second.
print("New list content:", numbers)  # Printing current list content.
```
The value inside the brackets which selects one element of the list is called an **index**, while the operation of selecting an element from the list is known as **indexing**.

> [!NOTE]
>All the indices used so far are literals. Their values are fixed at runtime, but **any expression can be the index, too**. This opens up lots of possibilities.

### Accessing list content
Each of the list's elements may be accessed separately. For example, it can be printed:
```python
print(numbers[0]) # Accessing the list's first element.
```
Assuming that all of the previous operations have been completed successfully, the snippet will send `111` to the console.

As you can see in the editor, the list may also be printed as a whole - just like here:
```python
print(numbers)  # Printing the whole list.
```
As you've probably noticed before, Python decorates the output in a way that suggests that all the presented values form a list. The output from the example snippet above looks like this:
```
[111, 1, 7, 2, 1]
```
### The len() function
The **length of a list** may vary during execution. New elements may be added to the list, while others may be removed from it. This means that the list is a very dynamic entity.

If you want to check the list's current length, you can use a function named `len()` (its name comes from _length_).

The function takes the **list's name as an argument, and returns the number of elements currently stored** inside the list (in other words - the list's length).
```python
numbers = [10, 5, 7, 2, 1]
print("Original list content:", numbers)  # Printing original list content.

numbers[0] = 111
print("\nPrevious list content:", numbers)  # Printing previous list content.

numbers[1] = numbers[4]  # Copying value of the fifth element to the second.
print("Previous list content:", numbers)  # Printing previous list content.

print("\nList length:", len(numbers))  # Printing the list's length.
```
### Removing elements from a list
Any of the list's elements may be **removed** at any time - this is done with an instruction named `del` (delete).
> [!NOTE]
> it's an instruction, not a function.

You have to point to the element to be removed - it'll vanish from the list, and the list's length will be reduced by one.
```python
del numbers[1]
print(len(numbers))
print(numbers)
```
**You can't access an element which doesn't exist** - you can neither get its value nor assign it a value. Both of these instructions will cause runtime errors now:
```python
print(numbers[4])
numbers[4] = 1
```
> We've removed one of the list's elements - there are only four elements in the list now. This means that element number four doesn't exist

### Negative indices are legal
It may look strange, but negative indices are legal, and can be very useful.

An element with an index equal to `-1` is **the last one in the list**.
```python
numbers = [111, 7, 2, 1]
```
An element with an index equal to `-1` is the last one in the list.
```python
print(numbers[-1])
```
The example snippet will output `1`.

Similarly, the element with an index equal to `-2` is the one before last in the list.
```python
print(numbers[-2])
```
The example snippet will output `2`.

The last accessible element in our list is `numbers[-4]` (the first one) - don't try to go any further!

## Functions vs. methods
**A method is a specific kind of function** - it behaves like a function and looks like a function, but differs in the way in which it acts, and in its invocation style.

A **function doesn't belong to any data** - it gets data, it may create new data and it (generally) produces a result.

A method does all these things, but is also able to **change the state of a selected entity**.

**A method is owned by the data it works for, while a function is owned by the whole code.**


This also means that invoking a method requires some specification of the data from which the method is invoked.

It may sound puzzling here, but we'll deal with it in depth when we delve into object-oriented programming.

In general, a typical function invocation may look like this:
```
result = function(arg)
```
The function takes an argument, does something, and returns a result.

A typical method invocation usually looks like this:
```
result = data.method(arg)
```

> [!NOTE]
>The name of the method is preceded by the name of the data which owns the method. Next, you **add** a dot, followed by the **method name**, and a **pair of parenthesis enclosing the arguments**.

The method will behave like a function, but can do something more - **it can change the internal state of the data** from which it has been invoked.

### Adding elements to a list: `append()` and `insert()`
A new element may be _glued_ to the end of the existing list:
```
list.append(value)
```
Such an operation is performed by a method named `append()`. It takes its argument's value and **puts it at the end of the list** which owns the method.

The list's length then increases by one.

The `insert()` method is a bit smarter - it can add a new element **at any place in the list**, not only at the end.
```
list.insert(location, value)
```
It takes two arguments:
- the first shows the required location of the element to be inserted; note: all the existing elements that occupy locations to the right of the new element (including the one at the indicated position) are shifted to the right, in order to make space for the new element;
- the second is the element to be inserted.
```python
numbers = [111, 7, 2, 1]
print(len(numbers))
print(numbers)

###

numbers.append(4)

print(len(numbers))
print(numbers)

###

numbers.insert(0, 222)
print(len(numbers))
print(numbers)
```

You can **start a list's life by making it empty** (this is done with an empty pair of square brackets) and then adding new elements to it as needed.

```python
my_list = []  # Creating an empty list.

for i in range(5):
    my_list.append(i + 1)

print(my_list)

```
Try to guess its output after the `for` loop execution. Run the program to check if you were right.

It'll be a sequence of consecutive integer numbers from `1` (you then add one to all the appended values) to `5`.

We've modified the snippet a bit:
```python
my_list = []  # Creating an empty list.

for i in range(5):
    my_list.insert(0, i + 1)

print(my_list)
```
what will happen now? Run the program and check if this time you were right, too.

You should get the same sequence, but in **reverse order** (this is the merit of using the `insert()` method).

### Making use of lists
The `for` loop has a very special variant that can `process lists` very effectively.

Let's assume that you want to **calculate the sum of all the values stored in the `my_list` list**.

You need a variable whose sum will be stored and initially assigned a value of `0` - its name will be `total`. (Note: we're not going to name it `sum` as Python uses the same name for one of its built-in functions - `sum()`. **Using the same name would generally be considered a bad practice**.) Then you add to it all the elements of the list using the `for` loop. Take a look at the snippet in the editor.

```python
my_list = [10, 1, 8, 3, 5]
total = 0

for i in range(len(my_list)):
    total += my_list[i]

print(total)
```
Let's comment on this example:
- the list is assigned a sequence of five integer values;
- the `i` variable takes the values `0`, `1`, `2`, `3`, and `4`, and then it indexes the list, selecting the subsequent elements: the first, second, third, fourth and fifth;
- each of these elements is added together by the `+=` operator to the `total` variable, giving the final result at the end of the loop;
- note the way in which the `len()` function has been employed - it makes the code independent of any possible changes in the list's content.

### The second face of the for loop
But the `for` loop can do much more. It can hide all the actions connected to the list's indexing, and deliver all the list's elements in a handy way.

This modified snippet shows how it works:
```python
my_list = [10, 1, 8, 3, 5]
total = 0

for i in my_list:
    total += i

print(total)
```
What happens here?
- the `for` instruction specifies the variable used to browse the list (`i` here) followed by the `in` keyword and the name of the list being processed (`my_list` here)
- the `i` variable is assigned the values of all the subsequent list's elements, and the process occurs as many times as there are elements in the list;
- this means that you use the `i` variable as a copy of the elements' values, and you don't need to use indices;
- the `len()` function is not needed here, either.

### Lists in action
Let's leave lists aside for a short moment and look at one intriguing issue.

Imagine that you need to rearrange the elements of a list, i.e., reverse the order of the elements: the first and the fifth as well as the second and fourth elements will be swapped. The third one will remain untouched.

Question: how can you swap the values of two variables?
```python
variable_1 = 1
variable_2 = 2

variable_2 = variable_1
variable_1 = variable_2
```
If you do something like this, you would **lose the value previously stored** in `variable_2`. Changing the order of the assignments will not help. You need a **third variable that serves as an auxiliary storage**.

This is how you can do it:
```python
variable_1 = 1
variable_2 = 2

auxiliary = variable_1
variable_1 = variable_2
variable_2 = auxiliary
```
Python offers a more convenient way of doing the swap - take a look:
```python
variable_1 = 1
variable_2 = 2

variable_1, variable_2 = variable_2, variable_1
```
Clear, effective and elegant - isn't it?

Now you can easily **swap** the list's elements to **reverse their order**:
```python
my_list = [10, 1, 8, 3, 5]

my_list[0], my_list[4] = my_list[4], my_list[0]
my_list[1], my_list[3] = my_list[3], my_list[1]

print(my_list)
```
Run the snippet. Its output should look like this:
```
[5, 3, 8, 1, 10]
```
It looks fine with five elements.

Will it still be acceptable with a list containing 100 elements? No, it won't.

Can you use the `for` loop to do the same thing automatically, irrespective of the list's length? Yes, you can.

This is how we've done it:
```python
my_list = [10, 1, 8, 3, 5]
length = len(my_list)

for i in range(length // 2):
    my_list[i], my_list[length - i - 1] = my_list[length - i - 1], my_list[i]

print(my_list)
```
Note:
- we've assigned the `length` variable with the current list's length (this makes our code a bit clearer and shorter)
- we've launched the `for` loop to run through its body `length // 2` times (this works well for lists with both even and odd lengths, because when the list contains an odd number of elements, the middle one remains untouched)
- we've swapped the i<sup>th</sup> element (from the beginning of the list) with the one with an index equal to `(length - i - 1)` (from the end of the list); in our example, for `i` equal to `0` the `(length - i - 1)` gives `4`; for `i` equal to `1`, it gives `3` ‒ this is exactly what we needed.

Lists are extremely useful, and you'll encounter them very often.

## Sorting a list
Python, however, has its own sorting mechanisms. No one needs to write their own sorts, as there is a sufficient number of **ready-to-use tools**.

If you want Python to sort your list, you can do it like this:
```python
my_list = [8, 10, 6, 2, 4]
my_list.sort()
print(my_list)
```
It is as simple as that.

The snippet's output is as follows:
```
[2, 4, 6, 8, 10]
```

As you can see, all the lists have a method named `sort()`, which sorts them as fast as possible. You've already learned about some of the list methods before, and you're going to learn more about others very soon

## The inner life of lists
```python
list_1 = [1]
list_2 = list_1
list_1[0] = 2
print(list_2)
```
The program:
- creates a one-element list named `list_1`;
- assigns it to a new list named `list_2`;
- changes the only element of `list_1`;
- prints out `list_2`.
The surprising part is the fact that the program will output: `[2]`, not `[1]`, which seems to be the obvious solution.


Lists (and many other complex Python entities) are stored in different ways than ordinary (scalar) variables.

You could say that:
- the name of an ordinary variable is the **name of its content**;
- the name of a list is the name of a **memory location where the list is stored**.

Read these two lines once more - the difference is essential for understanding what we are going to talk about next.

The assignment: `list_2 = list_1` copies the name of the array, not its contents. In effect, the two names (`list_1` and `list_2`) identify the same location in the computer memory. Modifying one of them affects the other, and vice versa.

How do you cope with that?

### Powerful slices
Fortunately, the solution is at your fingertips - its name is the **slice**.

A slice is an element of Python syntax that allows you to **make a brand new copy of a list, or parts of a list**.

It actually copies the list's contents, not the list's name.

This is exactly what you need. Take a look at the snippet below:
```python
list_1 = [1]
list_2 = list_1[:]
list_1[0] = 2
print(list_2)
```
Its output is `[1]`.

This inconspicuous part of the code described as `[:]` is able to produce a brand new list.

One of the most general forms of the slice looks as follows:
```python
my_list[start:end]
```
As you can see, it resembles indexing, but the colon inside makes a big difference.

A slice of this form **makes a new (target) list, taking elements from the source list - the elements of the indices from start to `end - 1`**.

> [!NOTE]
> Not to end `but` to `end - 1`. An element with an index equal to `end` is the first element which **does not take part in the slicing**.

Using negative values for both start and end is possible (just like in indexing).

Take a look at the snippet:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[1:3]
print(new_list)
```
The `new_list` list will have `end - start` (3 - 1 = 2) elements - the ones with indices equal to `1` and `2` (but not `3`).

The snippet's output is: `[8, 6]`

### Slices - negative indices
Look at the snippet below:
```python
my_list[start:end]
```
To repeat:
- `start` is the index of the first element **included in the slice**;
- `end` is the index of the first element **not included in the slice**.

This is how **negative indices** work with the slice:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[1:-1]
print(new_list)
```
The snippet's output is:
```
[8, 6, 4]
```
If the `start` specifies an element lying further than the one described by the `end` (from the list's beginning point of view), the slice will be **empty**:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[-1:1]
print(new_list)
```
The snippet's output is: `[]`

If you omit the `start` in your slice, it is assumed that you want to get a slice beginning at the element with index `0`.

In other words, the slice of this form:
```python
my_list[:end]
```
is a more compact equivalent of:
```python
my_list[0:end]
```
Look at the snippet below:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[:3]
print(new_list)
```
This is why its output is: `[10, 8, 6]`.

Similarly, if you omit the `end` in your slice, it is assumed that you want the slice to end at the element with the index `len(my_list)`.

In other words, the slice of this form:
```python
my_list[start:]
```
is a more compact equivalent of:
```python
my_list[start:len(my_list)]
```
Look at the following snippet:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[3:]
print(new_list)
```
Its output is therefore: `[4, 2]`.

As we've said before, omitting both `start` and `end` makes a **copy of the whole list**:
```python
my_list = [10, 8, 6, 4, 2]
new_list = my_list[:]
print(new_list)
```
The snippet's output is: `[10, 8, 6, 4, 2]`.

The previously described `del` instruction is able to **delete more than just a list's element at once - it can delete slices too**:
```python
my_list = [10, 8, 6, 4, 2]
del my_list[1:3]
print(my_list)
```
> [!NOTE]
> In this case, the slice doesn't produce any new list!

The snippet's output is: `[10, 4, 2]`.

Deleting all the elements at once is possible too:
```python
my_list = [10, 8, 6, 4, 2]
del my_list[:]
print(my_list)
```
The list becomes empty, and the output is: `[]`.

Removing the slice from the code changes its meaning dramatically.

Take a look:
```python
my_list = [10, 8, 6, 4, 2]
del my_list
print(my_list)
```
The `del` instruction will **delete the list itself, not its content**.

The `print()` function invocation from the last line of the code will then cause a runtime error.

## The in and not in operators
Python offers two very powerful operators, able to **look through the list in order to check whether a specific value is stored inside the list or not**.

These operators are:
```python
elem in my_list
elem not in my_list
```
The first of them (`in`) checks if a given element (its left argument) is currently stored somewhere inside the list (the right argument) - the operator returns `True` in this case.

The second (`not in`) checks if a given element (its left argument) is absent in a list - the operator returns `True` in this case.
```python
my_list = [0, 3, 12, 8, 2]

print(5 in my_list)
print(5 not in my_list)
print(12 in my_list)
```
