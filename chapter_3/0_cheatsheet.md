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


### Loops
1. There are two types of loops in Python: `while` and `for`:
- the `while` loop executes a statement or a set of statements as long as a specified boolean condition is true, e.g.:
    ```python
    # Example 1
    while True:
        print("Stuck in an infinite loop.")
    
    # Example 2
    counter = 5
    while counter > 2:
        print(counter)
        counter -= 1
    ```
- the `for` loop executes a set of statements many times; it's used to iterate over a sequence (e.g., a list, a dictionary, a tuple, or a set - you will learn about them soon) or other objects that are iterable (e.g., strings). You can use the `for` loop to iterate over a sequence of numbers using the built-in `range` function. Look at the examples below:
    ```python
    # Example 1
    word = "Python"
    for letter in word:
        print(letter, end="*")
    
    # Example 2
    for i in range(1, 10):
        if i % 2 == 0:
            print(i)
    ```
2. You can use the `break` and `continue` statements to change the flow of a loop:
- You use `break` to exit a loop, e.g.:
    ```python
    text = "OpenEDG Python Institute"
    for letter in text:
        if letter == "P":
            break
        print(letter, end="")
    ```
- You use `continue` to skip the current iteration, and continue with the next iteration, e.g.:
    ```python
    text = "pyxpyxpyx"
    for letter in text:
        if letter == "x":
            continue
        print(letter, end="")
    ```
3. The `while` and `for` loops can also have an `else` clause in Python. The `else` clause executes after the loop finishes its execution as long as it has not been terminated by `break`, e.g.:
    ```python
    n = 0
    
    while n != 3:
        print(n)
        n += 1
    else:
        print(n, "else")
    
    print()
    
    for i in range(0, 3):
        print(i)
    else:
        print(i, "else")
    ```

4. The `range()` function generates a sequence of numbers. It accepts integers and returns range objects. The syntax of `range()` looks as follows: `range(start, stop, step)`, where:
- `start` is an optional parameter specifying the starting number of the sequence (0 by default)
- `stop` is an optional parameter specifying the end of the sequence generated (it is not included),
- and `step` is an optional parameter specifying the difference between the numbers in the sequence (1 by default.)

    Example code:
    ```python
    for i in range(3):
        print(i, end=" ")  # Outputs: 0 1 2
    
    for i in range(6, 1, -2):
        print(i, end=" ")  # Outputs: 6, 4, 2
    ```

### Computer logic
1. Python supports the following logical operators:
- `and` → if both operands are true, the condition is true, e.g., `(True and True)` is `True`,
- `or` → if any of the operands are true, the condition is true, e.g., `(True or False)` is `True`,
- `not` → returns false if the result is true, and returns true if the result is false, e.g., `not True` is `False`.
2. You can use bitwise operators to manipulate single bits of data. The following sample data:
- `x = 15`, which is `0000 1111` in binary,
- `y = 16`, which is `0001 0000` in binary.

will be used to illustrate the meaning of bitwise operators in Python. Analyze the examples below:

- `&` does a bitwise and, e.g., `x & y = 0`, which is `0000 0000` in binary,
- `|` does a bitwise or, e.g., `x | y = 31`, which is `0001 1111` in binary,
- `˜`  does a bitwise not, e.g., `˜x = 240`, which is `1111 0000` in binary,
  - `-16` (decimal from signed 2's complement) -- read more about the [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) operation.
- `^` does a bitwise xor, e.g., `x ^ y = 31`, which is `0001 1111` in binary,
- `>>` does a bitwise right shift, e.g., `y >> 1 = 8`, which is `0000 1000` in binary,
- `<<` does a bitwise left shift, e.g., `y << 3 = 128`, which is `1000 0000` in binary,

### Lists
1. The **list is a type of data** in Python used to **store multiple objects**. It is an **ordered and mutable collection** of comma-separated items between square brackets, e.g.:
    ```python
    my_list = [1, None, True, "I am a string", 256, 0]
    ```
2. Lists can be **indexed and updated**, e.g.:
    ```python
    my_list = [1, None, True, 'I am a string', 256, 0]
    print(my_list[3])  # outputs: I am a string
    print(my_list[-1])  # outputs: 0
    
    my_list[1] = '?'
    print(my_list)  # outputs: [1, '?', True, 'I am a string', 256, 0]
    
    my_list.insert(0, "first")
    my_list.append("last")
    print(my_list)  # outputs: ['first', 1, '?', True, 'I am a string', 256, 0, 'last']
    ```
3. Lists can be **nested**, e.g.:
    ```python
    my_list = [1, 'a', ["list", 64, [0, 1], False]]
    ```
4. List elements and lists can be **deleted**, e.g.:
    ```python
    my_list = [1, 2, 3, 4]
    del my_list[2]
    print(my_list)  # outputs: [1, 2, 4]
    
    del my_list  # deletes the whole list
    ```
5. Lists can be **iterated** through using the `for` loop, e.g.:
    ```python
    my_list = ["white", "purple", "blue", "yellow", "green"]
    
    for color in my_list:
        print(color)
    ```
6. The `len()` function may be used to **check the list's length**, e.g.:
    ```python
    my_list = ["white", "purple", "blue", "yellow", "green"]
    print(len(my_list))  # outputs 5
    
    del my_list[2]
    print(len(my_list))  # outputs 4
    ```
7. A typical **function** invocation looks as follows: `result = function(arg)`, while a typical **method** invocation looks like this: **result = data.method(arg)**.
8. You can use the `sort()` method to sort elements of a list, e.g.:
    ```python
    lst = [5, 3, 1, 2, 4]
    print(lst)
    
    lst.sort()
    print(lst)  # outputs: [1, 2, 3, 4, 5]
    ```
9. There is also a list method called `reverse()`, which you can use to reverse the list, e.g.:
    ```python
    lst = [5, 3, 1, 2, 4]
    print(lst)
    
    lst.reverse()
    print(lst)  # outputs: [4, 2, 1, 3, 5]
    ```
10. If you have a list `l1`, then the following assignment: `l2 = l1` does not make a copy of the `l1` list, but makes the variables `l1` and `l2` **point to one and the same list in memory**. For example:
    ```python
    vehicles_one = ['car', 'bicycle', 'motor']
    print(vehicles_one) # outputs: ['car', 'bicycle', 'motor']
    
    vehicles_two = vehicles_one
    del vehicles_one[0] # deletes 'car'
    print(vehicles_two) # outputs: ['bicycle', 'motor']
    ```
11. If you want to copy a list or part of the list, you can do it by performing **slicing**:
    ```python
    colors = ['red', 'green', 'orange']
    
    copy_whole_colors = colors[:]  # copy the entire list
    copy_part_colors = colors[0:2]  # copy part of the list
    ```python
12. You can use **negative indices** to perform slices, too. For example:
    ```python
    sample_list = ["A", "B", "C", "D", "E"]
    new_list = sample_list[2:-1]
    print(new_list)  # outputs: ['C', 'D']
    ```
13. The `start` and `end` parameters are **optional** when performing a slice: `list[start:end]`, e.g.:
    ```python
    my_list = [1, 2, 3, 4, 5]
    slice_one = my_list[2: ]
    slice_two = my_list[ :2]
    slice_three = my_list[-2: ]
    
    print(slice_one)  # outputs: [3, 4, 5]
    print(slice_two)  # outputs: [1, 2]
    print(slice_three)  # outputs: [4, 5]
    ```
14. You can **delete slices** using the `del` instruction:
    ```python
    my_list = [1, 2, 3, 4, 5]
    del my_list[0:2]
    print(my_list)  # outputs: [3, 4, 5]
    
    del my_list[:]
    print(my_list)  # deletes the list content, outputs: []
    ```
6. You can test if some items **exist in a list or not** using the keywords `in` and `not in`, e.g.:
    ```python
    my_list = ["A", "B", 1, 2]
    
    print("A" in my_list)  # outputs: True
    print("C" not in my_list)  # outputs: True
    print(2 not in my_list)  # outputs: False
    ```