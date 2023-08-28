# Operators

An **operator** is a symbol of the programming language, which is able to operate on the values.

For example, just as in arithmetic, the `+` (plus) sign is the operator which is able to **add** two numbers, giving the result of the addition.

We'll begin with the operators which are associated with the most widely recognizable arithmetic operations:

`+`, `-`, `*`, `/`, `//`, `%`, `**`

> Data and operators when connected together form **expressions**. The simplest expression is a literal itself.

## Arithmetic operators 
### exponentiation
A `**` (double asterisk) sign is an **exponentiation** (power) operator. Its left argument is the **base**, its right, the **exponent**.

Classical mathematics prefers notation with superscripts, just like this: **2<sup>3</sup>**. Pure text editors don't accept that, so Python uses `**` instead, e.g., `2 ** 3`.

**Remember**: It's possible to formulate the following rules based on this result:
- when **both** `**` arguments are integers, the result is an integer, too;
- when **at least one** `**` argument is a float, the result is a float, too.

```python
print(2 ** 3)
print(2 ** 3.)
print(2. ** 3)
print(2. ** 3.)
```
> [!WARNING]
> The exponentiation operator uses right-sided binding

### multiplication
An `*` (asterisk) sign is a **multiplication** operator.

Run the code below and check if our integer vs. float rule is still working.
```python
print(2 * 3)
print(2 * 3.)
print(2. * 3)
print(2. * 3.)
```

### division
A `/` (slash) sign is a **divisional** operator.

The value in front of the slash is a **dividend**, the value behind the slash, a **divisor**.

Run the code below and analyze the results.
```python
print(6 / 3)
print(6 / 3.)
print(6. / 3)
print(6. / 3.)

```

You should see that there is an exception to the rule.

**The result produced by the division operator is always a float**, regardless of whether or not the result seems to be a float at first glance: `1 / 2`, or if it looks like a pure integer: `2 / 1`.

### integer division
A `//` (double slash) sign is an **integer divisional** operator. It differs from the standard `/` operator in two details:
- its result lacks the fractional part - it's absent (for integers), or is always equal to zero (for floats); this means that **the results are always rounded**;
- it conforms to the _integer vs. float rule_.

Run the example below and see the results:
```python
print(6 // 3)
print(6 // 3.)
print(6. // 3)
print(6. // 3.)
```

As you can see, integer by integer division gives an **integer result**. All other cases produce floats.

Let's do some more advanced tests.
```python
print(6 // 4)
print(6. // 4)
```
Imagine that we used `/` instead of `//` - could you predict the results?

Yes, it would be `1.5` in both cases. That's clear.

But what results should we expect with `//` division?
```python
1
1.0
```
What we get is two ones - one integer and one float.

The result of integer division is always rounded to the nearest integer value that is less than the real (not rounded) result.

> [!IMPORTANT]
> Rounding always goes to the lesser integer.

Look at the code below and try to predict the results once again:
```python
print(-6 // 4)
print(6. // -4)
```

Note: some of the values are negative. This will obviously affect the result. But how?

The result is two negative twos. The real (not rounded) result is `-1.5` in both cases. However, the results are the subjects of rounding. The **rounding goes toward the lesser integer value**, and the lesser integer value is `-2`, hence: `-2` and `-2.0`.

> [!NOTE]
> Integer division can also be called **floor division**.

### remainder (modulo)
Its graphical representation in Python is the `%` (percent) sign, which may look a bit confusing.

The result of the operator is a **remainder left after the integer division**.

In other words, it's the value left over after dividing one value by another to produce an integer quotient.

> The operator is sometimes called **modulo** in other programming languages.

Take a look at the snippet - try to predict its result and then run it:
```python
print(14 % 4)
```

As you can see, the result is two. This is why:
- `14 // 4` gives `3` → this is the integer **quotient**;
- `3 * 4` gives `12` → as a result of **quotient and divisor multiplication**;
- `14 - 12` gives `2` → this is the **remainder**.

This example is somewhat more complicated:
```python
print(12 % 4.5)
```
`3.0` - not `3` but `3.0` (**the rule still works**)

### addition
The **addition** operator is the `+` (plus) sign, which is fully in line with mathematical standards.

Again, take a look at the snippet of the program below:
```python
print(-4 + 4)
print(-4. + 8)
```

### The subtraction operator, unary and binary operators
The **subtraction** operator is obviously the `-` (minus) sign, although you should note that this operator also has another meaning - **it can change the sign of a number**.

This is a great opportunity to present a very important distinction between **unary** and **binary operators**.

In subtracting applications, the **minus operator expects two arguments**: the left (a **minuend** in arithmetical terms) and right (a **subtrahend**).

For this reason, the subtraction operator is considered to be one of the binary operators. 
But the minus operator may be used in a different (unary) way - take a look at the last line of the snippet below:
```python
print(-4 - 4)
print(4. - 8)
print(-1.1)
```

By the way: there is also a unary + operator. You can use it like this:
```python
print(+2)
```

The operator preserves the sign of its only argument - the right one.

Although such a construction is syntactically correct, using it doesn't make much sense, and it would be hard to find a good rationale for doing so.

## Operators and their bindings
The **binding** of the operator determines the order of computations performed by some operators with equal priority, put side by side in one expression.

Most of Python's operators have left-sided binding, which means that the calculation of the expression is conducted from left to right.
```python
print(9 % 6 % 2)
```
There are two possible ways of evaluating this expression:
- from left to right: first `9 % 6` gives `3`, and then `3 % 2` gives `1`;
- from right to left: first `6 % 2` gives `0`, and then `9 % 0` causes a **fatal error**.

The result should be `1`. This operator has **left-sided binding**. But there's one interesting exception.

Use this snippet of code:
```python
print(2 ** 2 ** 3)
```
The two possible results are:
- `2 ** 2` → `4`; `4 ** 3` → `64`
- `2 ** 3` → `8`; `2 ** 8` → `256`

The result clearly shows that **the exponentiation operator uses right-sided binding**.

## Operators and their priorities

Consider the following expression:
```python
2 + 3 * 5
```
You probably remember from school that **multiplications precede additions**.

The phenomenon that causes some operators to act before others is known as **the hierarchy of priorities**.

Python precisely defines the priorities of all operators, and assumes that operators of a larger (higher) priority perform their operations before the operators of a lower priority.

So, if you know that `*` has a higher priority than `+`, the computation of the final result should be obvious.

### List of priorities
Look at the table below:

| Priority | Operator |       |
|----------| --- |-------|
| 1 | `**` |       |
| 2 | `+`, `-` (note: unary operators located next to the right of the power operator bind more strongly) | unary |
| 3 | `*`, `/`, `//`, `%` |       |
| 4 | `+`, `-` | binary |

> Note: we've enumerated the operators in order **from the highest (1) to the lowest (4) priorities**.

Try to work through the following expression:
```python
print(2 * 3 % 5)
```

Both operators (`*` and `%`) have the same priority, so the result can be guessed only when you know the binding direction.

The result should be `1`

## Operators and parentheses
Of course, you're always allowed to use **parentheses**, which can change the natural order of a calculation.

In accordance with the arithmetic rules, **subexpressions in parentheses are always calculated first**.

You can use as many parentheses as you need, and they're often used to **improve the readability** of an expression, even if they don't change the order of the operations.

An example of an expression with multiple parentheses is here:
```python
print((5 * ((25 % 13) + 100) / (2 * 13)) // 2)
```

Try to compute the value that's printed to the console. What's the result of the `print()` function?

The result is `10.0`