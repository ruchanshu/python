# Literals or Data types in Python

A literal is data whose values are determined by the literal itself.

As this is a difficult concept to understand, a good example may be helpful.

Take a look at the following set of digits:

```python
123
```

Can you guess what value it represents? Of course you can - it's one hundred twenty three.

But what about this:

```python
c
```

And this is the clue: `123` is a literal, and `c` is not. You use literals to **encode data and to put them into your code**.

The numbers handled by modern computers are of two types:
- **integers**, that is, those which are devoid of the fractional part;
- and **floating-point** numbers (or simply **floats**), that contain (or are able to contain) the fractional part.

The characteristic of the numeric value which determines its kind, range, and application, is called the **type**.

If you encode a literal and place it inside Python code, the form of the literal determines the representation (type) Python will use to **store it in the memory**.

## Integers

The number eleven million one hundred and eleven thousand one hundred and eleven. you can write this number either like this: `11111111`, or like that: `11_111_111`

To code negative numbers in Python? As usual - by adding a **minus**. You can write: `-11111111`, or `-11_111_111`

Positive numbers do not need to be preceded by the plus sign, but it's permissible, if you wish to do it. The following lines describe the same number: `+11111111` and `11111111`.

- Python does allow the use of underscores in numeric literals.

> [!NOTE]
> Python 3.6 has introduced underscores in numeric literals, allowing for placing single underscores between digits and after base specifiers for improved readability. This feature is not available in older versions of Python.

## Octal numbers
If an integer number is preceded by an `0O` or `0o` prefix (zero-o), it will be treated as an octal value. This means that the number must contain digits taken from the [0..7] range only.

`0o123` is an **octal** number with a (decimal) value equal to `83`.

## Hexadecimal numbers

The second convention allows us to use **hexadecimal** numbers. Such numbers should be preceded by the prefix `0x` or `0X` (zero-x).

`0x123` is a **hexadecimal** number with a (decimal) value equal to `291`.

## Floats

To store the numbers that have a **non-empty decimal fraction**

```python
2.5
-0.4
```

> Note: two and a half looks normal when you write it in a program, although if your native language prefers to use a comma instead of a point in the number, you should ensure that your **number doesn't contain any commas** at all.

As you can probably imagine, the value of **zero point four** could be written in Python as:
```python
0.4
```
But don't forget this simple rule - you can omit zero when it is the only digit in front of or after the decimal point.

In essence, you can write the value 0.4 as:
```python
.4
```
For example: the value of 4.0 could be written as:
```python
4.
```
This will change neither its type nor its value.

### Scientific notation

Look at these two numbers:
```python
4
4.0
```

You may think that they are exactly the same, but Python sees them in a completely different way.

`4` is an **integer** number, whereas `4.0` is a **floating-point** number.

The point is what makes a float. It's not only points that make a float. You can also use the letter `e`.

When you want to use any numbers that are very large or very small, you can use **scientific notation**.

300000000 = 3 x 10<sup>8</sup>

In Python, the same effect is achieved in a slightly different way - take a look:
```python
3E8
```

The letter `E` (you can also use the lower-case letter `e` - it comes from the word **exponent**) is a concise record of the phrase _times ten to the power of_.

Note:
- the **exponent** (the value after the E) has to be an integer;
- the **base** (the value in front of the E) may be an integer.

Let's see how this convention is used to record numbers that are very small (in the sense of their absolute value, which is close to zero).

A physical constant called Planck's constant (and denoted as h), according to the textbooks, has the value of: **6.62607 x 10<sup>-34</sup>**

If you would like to use it in a program, you should write it this way:
```python
6.62607E-34
```

> The fact that you've chosen one of the possible forms of coding float values doesn't mean that Python will present it the same way.

When you run this literal through Python:
```python
print(0.0000000000000000000001)
```

this is the result:
```python
1e-22
```
Python always chooses **the more economical form of the number's presentation**, and you should take this into consideration when creating literals.

## Strings

You already know a bit about them, e.g., that **strings need quotes** the way floats need points.

This is a very typical string: `I am a string.`

Let's assume that we want to print a very simple message saying:
```
I like "Monty Python"
```
There are two possible solutions:
1. escape character
   - The backslash can escape quotes too. A quote preceded by a backslash changes its meaning - it's not a delimiter, but just a quote
   ```python
    print("I like \"Monty Python\"")
   ```

2. Python can use **an apostrophe instead of a quote**. Either of these characters may delimit strings, but you must be **consistent**.
   - If you open a string with a quote, you have to close it with a quote.
   - If you start a string with an apostrophe, you have to end it with an apostrophe.
   ```python
    print('I like "Monty Python"')
   ```

**A string can be empty** - it may contain no characters at all.
```python
''
""
```

## Boolean

The name comes from George Boole (1815-1864), the author of the fundamental work, _The Laws of Thought_, which contains the definition of **Boolean algebra** - a part of algebra which makes use of only two distinct values: `True` and `False`, denoted as `1` and `0`.

These two Boolean values have strict denotations in Python:
```python
True
False
```
You cannot change anything - you have to take these symbols as they are, including **case-sensitivity**.

Challenge: What will be the output of the following snippet of code?

```python
print(True > False)
print(True < False)
```