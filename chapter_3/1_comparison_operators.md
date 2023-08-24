# Comparison

### Equality: the equal to operator (==)
The `==` (equal to) operator compares the values of two operands. If they are equal, the result of the comparison is `True`. If they are not equal, the result of the comparison is `False`.

Don't forget this important distinction:

- `=` is an **assignment operator**, e.g., `a = b` assigns `a` with the value of `b`;
- `==` is the question are these values equal?; `a == b` **compares** `a` and `b`.

It is a **binary operator with left-sided binding**. It needs two arguments and **checks if they are equal**.

Question #2: What is the result of the following comparison?

`2 == 2.`

This question is not as easy as the first one. Luckily, Python is able to convert the integer value into its real equivalent, and consequently, the answer is `True`.

The question will be as follows:
```python
black_sheep == 2 * white_sheep
```
Due to the low priority of the `==` operator, the question shall be treated as equivalent to this one:
```python
black_sheep == (2 * white_sheep)
```
### Inequality: the not equal to operator (!=)
The `!=` (not equal to) operator compares the values of two operands, too. Here is the difference: if they are equal, the result of the comparison is `False`. If they are not equal, the result of the comparison is `True`.
```python
var = 0  # Assigning 0 to var
print(var != 0)

var = 1  # Assigning 1 to var
print(var != 0)
```
### Comparison operators: greater than
You can also ask a comparison question using the `>` (greater than) operator.
```python
black_sheep > white_sheep  # Greater than
```
`True` confirms it; `False` denies it.
### Comparison operators: greater than or equal to
The greater than operator has another special, **non-strict** variant, but it's denoted differently than in classical arithmetic notation: `>=` (greater than or equal to).

There are two subsequent signs, not one.

Both of these operators (strict and non-strict), as well as the two others discussed in the next section, are **binary operators with left-sided binding**, and their **priority is greater than that shown by `==` and `!=`**.

### Comparison operators: less than or equal to
As you've probably already guessed, the operators used in this case are: the `<` (less than) operator and its non-strict sibling: `<=` (less than or equal to).

**Making use of the answers**
 - **store it in a variable** and make use of it later
 - *make a decision about the future of the program*

### List of priorities
Look at the updated table below:

| Priority | Operator             |        |
|----------|----------------------|--------|
| 1        | `+`, `-`             | unary  |
| 2        | `**`                 |        |
| 3        | `*`, `/`, `//`, `%`  |        |
| 4        | `+`, `-`             | binary |
| 5        | `<`, `<=`, `>`, `>=` |        |
| 6        | `==`, `!=`           |        |