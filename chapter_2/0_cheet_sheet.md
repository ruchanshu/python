## Summary

### Data Types
1. **Literals** are notations for representing some fixed values in code. Python has various types of literals - for example, a literal can be a number (numeric literals, e.g., `123`), or a string (string literals, e.g., "I am a literal.").
2. The **binary system** is a system of numbers that employs _2_ as the base. Therefore, a binary number is made up of 0s and 1s only, e.g., `1010` is _10_ in decimal.
3. **Octal** and **hexadecimal** numeration systems, similarly, employ _8_ and _16_ as their bases respectively. The hexadecimal system uses the decimal numbers and six extra letters.
4. **Integers** (or simply **int**s) are one of the numerical types supported by Python. They are numbers written without a fractional component, e.g., `256`, or `-1` (negative integers).
5. **Floating-point** numbers (or simply **float**s) are another one of the numerical types supported by Python. They are numbers that contain (or are able to contain) a fractional component, e.g., `1.27`.
6. To encode an apostrophe or a quote inside a string you can either use the escape character, e.g., `'I\'m happy.'`, or open and close the string using an opposite set of symbols to the ones you wish to encode, e.g., `"I'm happy."` to encode an apostrophe, and `'He said "Python", not "typhoon"'` to encode a (double) quote.
7. **Boolean values** are the two constant objects `True` and `False` used to represent truth values (in numeric contexts `1` is `True`, while `0` is `False`.

> [!IMPORTANT]
> There is one more, special literal that is used in Python: the `None` literal. This literal is a so-called `NoneType` object, and it is used to represent **the absence of a value**. We'll tell you more about it soon.

### Operators
1. An **expression** is a combination of values (or variables, operators, calls to functions ‒ you will learn about them soon) which evaluates to a certain value, e.g., `1 + 2`.
2. **Operators** are special symbols or keywords which are able to operate on the values and perform (mathematical) operations, e.g., the `*` operator multiplies two values: `x * y`.
3. Arithmetic operators in Python: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (classic division ‒ always returns a float), `%` (modulus ‒ divides left operand by right operand and returns the remainder of the operation, e.g., `5 % 2 = 1`), `**` (exponentiation ‒ left operand raised to the power of right operand, e.g., `2 ** 3 = 2 * 2 * 2 = 8`), `//` (floor/integer division ‒ returns a number resulting from division, but rounded down to the nearest whole number, e.g., `3 // 2.0 = 1.0`)
4. A **unary** operator is an operator with only one operand, e.g., `-1`, or `+3`.
5. A **binary** operator is an operator with two operands, e.g., `4 + 5`, or `12 % 5`.
6. Some operators act before others – the hierarchy of priorities:
   - the `**` operator (exponentiation) has **the highest priority**;
   - then the unary `+` and `-` (note: a unary operator to the right of the exponentiation operator binds more strongly, for example: `4 ** -1` equals `0.25`)
   - then `*`, `/`, `//`, and `%`;
   - and, finally, the lowest priority: the binary `+` and `-`.
7. Subexpressions in **parentheses** are always calculated first, e.g., `15 - 1 * (5 * (1 + 2)) = 0`.
8. The **exponentiation** operator uses **right-sided binding**, e.g., `2 ** 2 ** 3 = 256`.

### Variables
1. A **variable** is a named location reserved to store values in the memory. A variable is created or initialized automatically when you assign a value to it for the first time.
2. Each variable must have a unique name - an **identifier**. A legal identifier name must be a non-empty sequence of characters, must begin with the underscore(`_`), or a letter, and it cannot be a Python keyword. The first character may be followed by underscores, letters, and digits. Identifiers in Python are case-sensitive.
3. Python is a **dynamically-typed** language, which means you don't need to declare variables in it. (2.1.4.3) To assign values to variables, you can use a simple assignment operator in the form of the equal (`=`) sign, i.e., `var = 1`.
4. You can also use **compound assignment operators** (shortcut operators) to modify values assigned to variables, e.g., 1, or `var /= 5 * 2`.
5. You can assign new values to already existing variables using the assignment operator or one of the compound operators.
   ```python
   var = 2
   print(var)
   
   var = 3
   print(var)
   
   var += 1
   print(var)
   ```
6. You can combine text and variables using the `+` operator, and use the `print()` function to output strings and variables.
   ```python
   var = "007"
   print("Agent " + var)
   ```
   
### Comments
1. Comments can be used to leave additional information in code. They are omitted at runtime. The information left in source code is addressed to human readers. In Python, a comment is a piece of text that begins with `#`. The comment extends to the end of line.
2. If you want to place a comment that spans several lines, you need to place `#` in front of them all. Moreover, you can use a comment to mark a piece of code that is not needed at the moment (see the last line of the snippet below), e.g.:
   ```python
   # This program prints
   # an introduction to the screen.
   print("Hello!")  # Invoking the print() function
   # print("I'm Python.")
   ```
3. Whenever possible and justified, you should give **self-commenting names** to variables, e.g., if you're using two variables to store a length and width of something, the variable names `length` and `width` may be a better choice than `myvar1` and `myvar2`.
4. It's important to use comments to make programs easier to understand, and to use readable and meaningful variable names in code. However, it's equally important **not to use** variable names that are confusing, or leave comments that contain wrong or incorrect information!
5. Comments can be important when you are reading your own code after some time (trust us, developers do forget what their own code does), and when others are reading your code (can help them understand what your programs do and how they do it more quickly).