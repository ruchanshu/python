## Summary

### Comparison operators and Conditional statement
1. The **comparison** (otherwise known as relational) operators are used to compare values. The table below illustrates how the comparison operators work, assuming that `x = 0`, `y = 1`, and `z = 0`:

   | Operator | Description | Example                                        |
   |----------|------------------------------------------------|--------|
   | `==`     | returns `True` if operands' values are equal, and `False` otherwise |                                                |
   | `!=`     | returns `True` if operands' values are not equal, and `False` otherwise| ```x != y  # True``` <br/> ```x != z  # False``` |
   | `>`      | `True` if the left operand's value is greater than the right operand's value, and `False` otherwise | ```x > y  # False``` <br/> ```y > z  # True``` |
   | `<`      | `True` if the left operand's value is less than the right operand's value, and `False` otherwise | ```x < y  # True``` <br/> ```y < z  # False``` |
   | `≥`      | `True` if the left operand's value is greater than or equal to the right operand's value, and `False` otherwise | ```x >= y  # False``` <br/> ```x >= z  # True``` <br/> ```y >= z  # True``` |
   | `≤`      | `True` if the left operand's value is less than or equal to the right operand's value, and `False` otherwise | ```x <= y  # True``` <br/> ```x <= z  # True``` <br/> ```y <= z  # False``` |

2. When you want to execute some code only if a certain condition is met, you can use a **conditional statement**:

- a single `if` statement, e.g.:
  ```python
  x = 10

  if x == 10: # condition
      print("x is equal to 10")  # Executed if the condition is True.
  ```
- a series of `if` statements, e.g.:
  ```python
  x = 10

  if x > 5: # condition one
      print("x is greater than 5")  # Executed if condition one is True.
   
  if x < 10: # condition two
      print("x is less than 10")  # Executed if condition two is True.
   
  if x == 10: # condition three
      print("x is equal to 10")  # Executed if condition three is True. 
  ```
  Each `if` statement is tested separately.

- an `if-else` statement, e.g.:
  ```python
  x = 10

  if x < 10:  # Condition
      print("x is less than 10")  # Executed if the condition is True.
   
  else:
      print("x is greater than or equal to 10")  # Executed if the condition is False.
  ```
- a series of `if` statements followed by an `else`, e.g.:
  ```python
  x = 10
   
  if x > 5:  # True
      print("x > 5")
   
  if x > 8:  # True
      print("x > 8")
   
  if x > 10:  # False
      print("x > 10")
   
  else:
      print("else will be executed")
  ```
  Each `if` is tested separately. The body of `else` is executed if the last `if` is `False`.

- The `if-elif-else` statement, e.g.:
  ```python
  x = 10
   
  if x == 10:  # True
      print("x == 10")
   
  if x > 15:  # False
      print("x > 15")
   
  elif x > 10:  # False
      print("x > 10")
   
  elif x > 5:  # True
      print("x > 5")
   
  else:
      print("else will not be executed")
  ```
  If the condition for `if` is `False`, the program checks the conditions of the subsequent `elif` blocks – the first `elif` block that is `True` is executed. If all the conditions are `False`, the `else` block will be executed.
   
- Nested conditional statements, e.g.:
  ```python
  x = 10
   
  if x > 5:  # True
      if x == 6:  # False
          print("nested: x == 6")
      elif x == 10:  # True
          print("nested: x == 10")
      else:
          print("nested: else")
  else:
      print("else")
  ```


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
