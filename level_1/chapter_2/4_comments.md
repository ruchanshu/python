# Comments 

A remark inserted into the program, which is **omitted at runtime**, is called a **comment**.

### Leaving comments in code: why, how, and when

Whenever Python encounters a comment in your program, the comment is completely transparent to it - from Python's point of view, this is only one space (regardless of how long the real comment is).

In Python, a comment is a piece of text that begins with a `#` (hash) sign and extends to the end of the line.

If you want a comment that spans several lines, you have to put a hash in front of them all.
```python
# This program evaluates the hypotenuse c.
# a and b are the lengths of the legs.
a = 3.0
b = 4.0
c = (a ** 2 + b ** 2) ** 0.5  # We use ** instead of square root.
print("c =", c)
```

Good, responsible developers **describe each important piece of code**, e.g., explaining the role of the variables; although it must be stated that the best way of commenting variables is to name them in an unambiguous manner.

For example, if a particular variable is designed to store an area of some unique square, the name `square_area` will obviously be better than `aunt_jane`.

We say that the first name is **self-commenting**.

Comments may be useful in another respect - you can use them to **mark a piece of code that currently isn't needed** for whatever reason. Look at the example below, if you **uncomment** the highlighted line, this will affect the output of the code:
```python
# This is a test program.
x = 1
y = 2
# y = y + x
print(x + y)
```
This is often done during the testing of a program, in order to isolate the place where an error might be hidden.