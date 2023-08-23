# Type casting
Python offers two simple functions to specify a type of data and solve this problem - here they are: `int()` and `float()`.

Their names are self-commenting:
- the `int()` function **takes one argument** (e.g., a string: `int(string)`) and tries to convert it into an integer; if it fails, the whole program will fail too (there is a workaround for this situation, but we'll show you this a little later);
- the `float()` function takes one argument (e.g., a string: `float(string)`) and tries to convert it into a float (the rest is the same).

This is very simple and very effective. Moreover, you can invoke any of the functions by passing the `input()` results directly to them. There's no need to use any variable as an intermediate storage.
```python
anything = float(input("Enter a number: "))
something = anything ** 2.0
print(anything, "to the power of 2 is", something)
```
Try to run the modified code. Don't forget to enter a **valid number**.

Check some different values, small and big, negative and positive. Zero is a good input, too.

As the `print()` function accepts an expression as its argument, you can **remove the variable** from the code.

Just like this:
```python
anything = float(input("Enter a number: "))
print(anything, "to the power of 2 is", anything ** 2.0)
```

### Type conversion: str()
You can also convert a **number into a string**, which is way easier and safer ‒ this kind of operation is always possible.

A function capable of doing that is called `str()`:
```python
str(number)
```