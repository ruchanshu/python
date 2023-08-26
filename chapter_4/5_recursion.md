# Recursion

Are you familiar with **Fibonacci numbers**?

They are a **sequence of integer numbers** built using a very simple rule:
- the first element of the sequence is equal to one (**Fib<sub>1</sub>** = 1)
- the second is also equal to one (**Fib<sub>2</sub>** = 1)
- every subsequent number is the the_sum of the two preceding numbers:
   
  (**Fib<sub>i</sub>** = **Fib<sub>i - 1</sub>** + **Fib<sub>i - 2</sub>**)
  
Here are some of the first Fibonacci numbers:
```
fib_1 = 1
fib_2 = 1
fib_3 = 1 + 1 = 2
fib_4 = 1 + 2 = 3
fib_5 = 2 + 3 = 5
fib_6 = 3 + 5 = 8
fib_7 = 5 + 8 = 13
```

What do you think about **implementing this as a function**?

Let's create our `fib` function and test it. Here it is:
```python
def fib(n):
    if n < 1:
        return None
    if n < 3:
        return 1

    elem_1 = elem_2 = 1
    the_sum = 0
    for i in range(3, n + 1):
        the_sum = elem_1 + elem_2
        elem_1, elem_2 = elem_2, the_sum
    return the_sum


for n in range(1, 10):  # testing
    print(n, "->", fib(n))
```
Analyze the `for` loop body carefully, and find out how we **move the `elem_1` and `elem_2` variables through the subsequent Fibonacci numbers**.

The test part of the code produces the following output:
```
1 -> 1
2 -> 1
3 -> 2
4 -> 3
5 -> 5
6 -> 8
7 -> 13
8 -> 21
9 -> 34
```

### recursion
There's one more thing we want to show you to make everything complete - it's **recursion**.

In this field, recursion is a **technique where a function invokes itself**.

These two cases seem to be the best to illustrate the phenomenon - factorials and Fibonacci numbers. Especially the latter.

**The Fibonacci numbers definition is a clear example of recursion**. We already told you that:

**Fib<sub>i</sub> = Fib<sub>i-1</sub> + Fib<sub>i-2</sub>**

The definition of the ith number refers to the i-1 number, and so on, till you reach the first two.

Can it be used in the code? Yes, it can. It can also make the code shorter and clearer.

The second version of our `fib()` function makes direct use of this definition:
```python
def fib(n):
    if n < 1:
        return None
    if n < 3:
        return 1
    return fib(n - 1) + fib(n - 2)
```
The code is much clearer now.

But is it really safe? Does it entail any risk?

Yes, there is a little risk indeed. **If you forget to consider the conditions which can stop the chain of recursive invocations, the program may enter an infinite loop.** You have to be careful.

***
The factorial has a second, **recursive** side too. Look:
```python
def factorial_function(n):
    if n < 0:
        return None
    if n < 2:
        return 1
    
    product = 1
    for i in range(2, n + 1):
        product *= i
    return product


for n in range(1, 6):  # testing
    print(n, factorial_function(n))
```

n! = 1 × 2 × 3 × ... × n-1 × n

It's obvious that:

1 × 2 × 3 × ... × n-1 = (n-1)!

So, finally, the result is:

n! = (n-1)! × n

This is in fact a ready recipe for our new solution.

Here it is:
```python
def factorial_function(n):
    if n < 0:
        return None
    if n < 2:
        return 1
    return n * factorial_function(n - 1)
```
Does it work? Yes, it does. Try it for yourself.