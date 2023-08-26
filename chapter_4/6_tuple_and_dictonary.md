# Tuples and dictionaries

### Sequence types and mutability
Before we start talking about **tuples** and **dictionaries**, we have to introduce two important concepts: **sequence types** and **mutability**.

A **sequence type is a type of data in Python which is able to store more than one value (or less than one, as a sequence may be empty), and these values can be sequentially (hence the name) browsed**, element by element.

As the `for` loop is a tool especially designed to iterate through sequences, we can express the definition as: **a sequence is data which can be scanned by the `for` loop**.

You've encountered one Python sequence so far - the list. The list is a classic example of a Python sequence, although there are some other sequences worth mentioning, and we're going to present them to you now.

The second notion - **mutability** - is a property of any of Python's data that describes its readiness to be freely changed during program execution. There are two kinds of Python data: **mutable** and **immutable**.

**Mutable data can be freely updated at any time** - we call such an operation in situ.

In situ is a Latin phrase that translates as literally in position. For example, the following instruction modifies the data in situ:
```python
list.append(1)
```
**Immutable data cannot be modified in this way.**

Imagine that a list can only be assigned and read over. You would be able neither to append an element to it, nor remove any element from it. This means that appending an element to the end of the list would require the recreation of the list from scratch.

You would have to build a completely new list, consisting of the all elements of the already existing list, plus the new element.

The data type we want to tell you about now is a tuple. **A tuple is an immutable sequence type**. It can behave like a list, but it mustn't be modified in situ.

## What is a tuple?
The first and the clearest distinction between lists and tuples is the syntax used to create them - **tuples prefer to use parenthesis**, whereas lists like to see brackets, although it's also **possible to create a tuple just from a set of values separated by commas**.

Look at the example:
```python
tuple_1 = (1, 2, 4, 8)
tuple_2 = 1., .5, .25, .125

print(tuple_1)
print(tuple_2)
```
There are two tuples, both containing **four elements**.

This is what you should see in the console:
```
(1, 2, 4, 8)
(1.0, 0.5, 0.25, 0.125)
```
> [!NOTE]
> Each tuple element may be of a different type (floating-point, integer, or any other not-as-yet-introduced kind of data).

### How to create a tuple?
It is possible to create an empty tuple - parentheses are required then:
```python
empty_tuple = ()
```
If you want to create a **one-element tuple**, you have to take into consideration the fact that, due to syntax reasons (a tuple has to be distinguishable from an ordinary, single value), you must end the value with a comma:
```python
one_element_tuple_1 = (1, )
one_element_tuple_2 = 1.,
```
Removing the commas won't spoil the program in any syntactical sense, but you will instead get two single variables, not tuples.

### How to use a tuple?
If you want to get the elements of a tuple in order to read them over, you can use the same conventions to which you're accustomed while using lists.
```python
my_tuple = (1, 10, 100, 1000)

print(my_tuple[0])
print(my_tuple[-1])
print(my_tuple[1:])
print(my_tuple[:-2])

for elem in my_tuple:
    print(elem)
```
The program should produce the following output - run it and check:
```
1
1000
(10, 100, 1000)
(1, 10)
1
10
100
1000
```
The similarities may be misleading - **don't try to modify a tuple's contents!** It's not a list!

All of these instructions (except the topmost one) will cause a runtime error:
```python
my_tuple = (1, 10, 100, 1000)

my_tuple.append(10000)
del my_tuple[0]
my_tuple[1] = -10
```
This is the message that Python will give you in the console window:
```
AttributeError: 'tuple' object has no attribute 'append'
```

What else can tuples do for you?
- the `len()` function accepts tuples, and returns the number of elements contained inside;
- the `+` operator can join tuples together
- the `*` operator can multiply tuples, just like lists;
- the `in` and `not in` operators work in the same way as in lists.

```python
my_tuple = (1, 10, 100)

t1 = my_tuple + (1000, 10000)
t2 = my_tuple * 3

print(len(t2))
print(t1)
print(t2)
print(10 in my_tuple)
print(-10 not in my_tuple)
```
The output should look as follows:
```
9
(1, 10, 100, 1000, 10000)
(1, 10, 100, 1, 10, 100, 1, 10, 100)
True
True
```
One of the most useful tuple properties is their ability to **appear on the left side of the assignment operator**. You saw this phenomenon some time ago, when it was necessary to find an elegant tool to swap two variables' values.

Take a look at the snippet below:
```python
var = 123

t1 = (1, )
t2 = (2, )
t3 = (3, var)

t1, t2, t3 = t2, t3, t1

print(t1, t2, t3)
```
It shows three tuples interacting - in effect, the values stored in them "circulate" - `t1` becomes `t2`, `t2` becomes `t3`, and `t3` becomes `t1`.

> [!NOTE]
> The example presents one more important fact: a **tuple's elements can be variables**, not only literals. Moreover, they can be expressions if they're on the right side of the assignment operator.

## What is a dictionary?
The **dictionary** is another Python data structure. It's **not a sequence type** (but can be easily adapted to sequence processing) and it is **mutable**.

In Python's world, the word you look for is named a `key`. The word you get from the dictionary is called a `value`.

This means that a dictionary is a set of **key-value** pairs. Note:
- each key must be **unique** - it's not possible to have more than one key of the same value;
- a key may be **any immutable type of object**: it can be a number (integer or float), or even a string, but not a list;
- a dictionary is not a list - a list contains a set of numbered values, while **a dictionary holds pairs of values**;
- the `len()` function works for dictionaries, too - it returns the numbers of key-value elements in the dictionary;
- a dictionary is a **one-way tool** - if you have an English-French dictionary, you can look for French equivalents of English terms, but not vice versa.

### How to make a dictionary?
If you want to assign some initial pairs to a dictionary, you should use the following syntax:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}
phone_numbers = {'boss': 5551234567, 'Suzy': 22657854310}
empty_dictionary = {}

print(dictionary)
print(phone_numbers)
print(empty_dictionary)
```
In the first example, the dictionary uses keys and values which are both strings. In the second one, the keys are strings, but the values are integers. The reverse layout (keys → numbers, values → strings) is also possible, as well as number-number combination.

The list of pairs is surrounded by **curly braces**, while the pairs themselves are **separated by commas**, and the **keys and values by colons**.

The first of our dictionaries is a very simple English-French dictionary. The second - a very tiny telephone directory.

The empty dictionaries are constructed by an **empty pair of curly braces** - nothing unusual.

The dictionary as a whole can be printed with a single `print()` invocation. The snippet **may** produce the following output:
```python
{'dog': 'chien', 'horse': 'cheval', 'cat': 'chat'}
{'Suzy': 5557654321, 'boss': 5551234567}
{}
```
Have you noticed anything surprising? The order of the printed pairs is different than in the initial assignment. What does that mean?

First of all, it's a confirmation that **dictionaries are not lists** - they don't preserve the order of their data, as the order is completely meaningless (unlike in real, paper dictionaries). The order in which a dictionary **stores its data is completely out of your control**, and your expectations. That's normal. (*)

> [!WARNING]
> In Python 3.6x dictionaries have become **ordered** collections by default. Your results may vary depending on what Python version you're using.

### How to use a dictionary?
If you want to get any of the values, you have to deliver a valid key value:
```python
print(dictionary['cat'])
print(phone_numbers['Suzy'])
```
Getting a dictionary's value resembles indexing, especially thanks to the brackets surrounding the key's value.

Note:
- if the key is a string, you have to specify it as a string;
- **keys are case-sensitive**: `Suzy` is something different from `suzy`.

The snippet outputs two lines of text:
```
chat
22657854310
```
And now the most important news: you **mustn't use a non-existent key**. Trying something like this:
```python
print(phone_numbers['president'])
```
will cause a runtime error. Try to do it.

Fortunately, there's a simple way to avoid such a situation. The `in` operator, together with its companion, `not in`, can salvage this situation.

The following code safely searches for some French words:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}
words = ['cat', 'lion', 'horse']

for word in words:
    if word in dictionary:
        print(word, "->", dictionary[word])
    else:
        print(word, "is not in dictionary")
```
The code's output looks as follows:
```
cat -> chat
lion is not in dictionary
horse -> cheval
```

When you write a big or lengthy expression, it may be a good idea to keep it vertically aligned. This is how you can make your code more readable and more programmer-friendly, e.g.:
```python
# Example 1:
dictionary = {
              "cat": "chat",
              "dog": "chien",
              "horse": "cheval"
              }

# Example 2:
phone_numbers = {'boss': 5551234567,
                 'Suzy': 22657854310
                 }

```
This kind of formatting is called a **hanging indent**.

### How to use a dictionary: the `keys()`
Can dictionaries be **browsed** using the `for` loop, like lists or tuples?

No and yes.

No, because a dictionary is **not a sequence type** - the `for` loop is useless with it.

Yes, because there are simple and very effective tools that can **adapt any dictionary to the `for` loop requirements** (in other words, building an intermediate link between the dictionary and a temporary sequence entity).

The first of them is a method named `keys()`, possessed by each dictionary. The method **returns an iterable object consisting of all the keys gathered within the dictionary**. Having a group of keys enables you to access the whole dictionary in an easy and handy way.

Just like here:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

for key in dictionary.keys():
    print(key, "->", dictionary[key]
```
The code's output looks as follows:
```
horse -> cheval
dog -> chien
cat -> chat
```

### The `sorted()` function
Do you want it **sorted**? Just enrich the `for` loop to get such a form:
```python
for key in sorted(dictionary.keys()):
```
The `sorted()` function will do its best - the output will look like this:
```
cat -> chat
dog -> chien
horse -> cheval
```

### How to use a dictionary: The `items()` and `values()` methods
Another way is based on using a dictionary's method named `items()`. The method **returns tuples** (this is the first example where tuples are something more than just an example of themselves) **where each tuple is a key-value pair**.

This is how it works:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

for english, french in dictionary.items():
    print(english, "->", french)
```
Note the way in which the tuple has been used as a `for` loop variable.

The example prints:
```
cat -> chat
dog -> chien
horse -> cheval
```

There is also a method named `values()`, which works similarly to `keys()`, but **returns values**.

Here is a simple example:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

for french in dictionary.values():
    print(french)
```
As the dictionary is not able to automatically find a key for a given value, the role of this method is rather limited.

Here is the expected output:
```
cheval
chien
chat
```

### How to use a dictionary: modifying and adding values
Assigning a new value to an existing key is simple - as dictionaries are fully **mutable**, there are no obstacles to modifying them.

We're going to replace the value `"chat"` with `"minou"`, which is not very accurate, but it will work well with our example.

Look:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

dictionary['cat'] = 'minou'
print(dictionary)
```
The output is:
```
{'cat': 'minou', 'dog': 'chien', 'horse': 'cheval'}
```

### Adding a new key
Adding a new key-value pair to a dictionary is as simple as changing a value - you only have to assign a value to a new, **previously non-existent key**.

> This is very different behavior compared to lists, which don't allow you to assign values to non-existing indices.

Let's add a new pair of words to the dictionary - a bit weird, but still valid:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

dictionary['swan'] = 'cygne'
print(dictionary)
```
The example outputs:
```
{'cat': 'chat', 'dog': 'chien', 'horse': 'cheval', 'swan': 'cygne'}
```

#### `update()` method
You can also insert an item to a dictionary by using the `update()` method, e.g.:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

dictionary.update({"duck": "canard"})
print(dictionary)
```

### Removing a key
Can you guess how to remove a key from a dictionary?

> [!NOTE]
> Removing a key will always cause the **removal of the associated value. Values cannot exist without their keys**.

This is done with the `del` instruction.

Here's the example:
```
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

del dictionary['dog']
print(dictionary)
```

> [!IMPORTANT]
> Removing a non-existing key causes an error.

The example outputs:
```
{'cat': 'chat', 'horse': 'cheval'}
```

#### `popitem()` method
To remove the last item in a dictionary, you can use the `popitem()` method:
```python
dictionary = {"cat": "chat", "dog": "chien", "horse": "cheval"}

dictionary.popitem()
print(dictionary)    # outputs: {'cat': 'chat', 'dog': 'chien'}
```
In the older versions of Python, i.e., before 3.6.7, the `popitem()` method removes a random item from a dictionary.

## Tuples and dictionaries can work together
We've prepared a simple example, showing how tuples and dictionaries can work together.

Let's imagine the following problem:

- you need a program to evaluate the students' average scores;
- the program should ask for the student's name, followed by her/his single score;
- the names may be entered in any order;
- entering an empty name finishes the inputting of the data (note 1: entering an empty score will raise the ValueError exception, but don't worry about that now, you'll see how to handle such cases when we talk about exceptions in the second part of the Python Essentials course series)
- a list of all names, together with the evaluated average score, should be then emitted.

```python
school_class = {}

while True:
    name = input("Enter the student's name: ")
    if name == '':
        break
    
    score = int(input("Enter the student's score (0-10): "))
    if score not in range(0, 11):
	    break
    
    if name in school_class:
        school_class[name] += (score,)
    else:
        school_class[name] = (score,)
        
for name in sorted(school_class.keys()):
    adding = 0
    counter = 0
    for score in school_class[name]:
        adding += score
        counter += 1
    print(name, ":", adding / counter)
```

Now, let's analyze it line by line:

- **line 1**: create an empty dictionary for the input data; the student's name is used as a key, while all the associated scores are stored in a tuple (the tuple may be a dictionary value - that's not a problem at all)
- **line 3**: enter an "infinite" loop (don't worry, it'll break at the right moment)
- **line 4**: read the student's name here;
- **line 5-6**: if the name is an empty string (""), leave the loop;
- **line 8**: ask for one of the student's scores (an integer from the range 0-10)
- **line 9-10**: if the score entered is not within the range from 0 to 10, leave the loop;
- **line 12-13**: if the student's name is already in the dictionary, lengthen the associated tuple with the new score (note the += operator)
- **line 14-15**: if this is a new student (unknown to the dictionary), create a new entry - its value is a one-element tuple containing the entered score;
- **line 17**: iterate through the sorted students' names;
- **line 18-19**: initialize the data needed to evaluate the average (sum and counter)
- **line 20-22**: we iterate through the tuple, taking all the subsequent scores and updating the sum, together with the counter;
- **line 23**: evaluate and print the student's name and average score.

This is a record of the conversation we had with our program:
```
Enter the student's name: Bob
Enter the student's score (0-10): 7
Enter the student's name: Andy
Enter the student's score (0-10): 3
Enter the student's name: Bob
Enter the student's score (0-10): 2
Enter the student's name: Andy
Enter the student's score (0-10): 10
Enter the student's name: Andy
Enter the student's score (0-10): 3
Enter the student's name: Bob
Enter the student's score (0-10): 9
Enter the student's name:
Andy : 5.333333333333333
Bob : 6.0
```