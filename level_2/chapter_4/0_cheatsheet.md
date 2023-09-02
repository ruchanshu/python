## Summary

### Generators and many more
1. An **iterator** is an object of a class providing at least **two** methods (not counting the constructor):
    - `__iter__()` is invoked once when the iterator is created and returns the iterator's object **itself**;
    - `__next__()` is invoked to provide the **next iteration's value** and raises the `StopIteration` exception when the iteration **comes to an end**.
2. The `yield` statement can be used only inside functions. The `yield` statement suspends function execution and causes the function to return the yield's argument as a result. Such a function cannot be invoked in a regular way – its only purpose is to be used as a **generator** (i.e. in a context that requires a series of values, like a `for` loop.)
3. A **conditional expression** is an expression built using the `if-else` operator. For example:
    ```python
    print(True if 0 >= 0 else False)
    ```
    outputs `True`.
4. A **list comprehension** becomes a **generator** when used inside **parentheses** (used inside brackets, it produces a regular list). For example:
    ```python
    for x in (el * 2 for el in range(5)):
        print(x)
    ```
    outputs `02468`.
5. A **lambda function** is a tool for creating **anonymous functions**. For example:
    ```python
    def foo(x, f):
        return f(x)
    
    print(foo(9, lambda x: x ** 0.5))
    ```
    outputs `3.0`.
6. The `map(fun, list)` function creates a **copy** of a `list` argument, and applies the `fun` function to all of its elements, returning a **generator** that provides the new list content element by element. For example:
    ```python
    short_list = ['mython', 'python', 'fell', 'on', 'the', 'floor']
    new_list = list(map(lambda s: s.title(), short_list))
    print(new_list)
    ```
    outputs `['Mython', 'Python', 'Fell', 'On', 'The', 'Floor']`.
7. The `filter(fun, list)` function creates a **copy** of those `list` elements, which cause the `fun` function to return `True`. The function's result is a **generator** providing the new list content element by element. For example:
   ```python
   short_list = [1, "Python", -1, "Monty"]
   new_list = list(filter(lambda s: isinstance(s, str), short_list))
   print(new_list)
   ```
   outputs `['Python', 'Monty']`.
8. A closure is a technique which allows the **storing of values** in spite of the fact that the **context** in which they have been created **does not exist anymore**. For example:
   ```python
   def tag(tg):
       tg2 = tg
       tg2 = tg[0] + '/' + tg[1:]
   
       def inner(str):
           return tg + str + tg2
       return inner
   
   
   b_tag = tag('<b>')
   print(b_tag('Monty Python'))
   ```
   outputs `<b>Monty Python</b>`

### Files
1. A file needs to be **open** before it can be processed by a program, and it should be **closed** when the processing is finished.

   Opening the file associates it with the **stream**, which is an abstract representation of the physical data stored on the media. The way in which the stream is processed is called **open mode**. Three open modes exist:
   - **read mode** – only read operations are allowed;
   - **write mode** – only write operations are allowed;
   - **update mode** – both writes and reads are allowed.
2. Depending on the physical file content, different Python classes can be used to process files. In general, the `BufferedIOBase` is able to process any file, while `TextIOBase` is a specialized class dedicated to processing text files (i.e. files containing human-visible texts divided into lines using new-line markers). Thus, the streams can be divided into **binary** and **text** ones.
3. The following `open()` function syntax is used to open a file:
   ```python
   open(file_name, mode=open_mode, encoding=text_encoding)
   ```
   The invocation creates a stream object and associates it with the file named `file_name`, using the specified `open_mode` and setting the specified `text_encoding`, or it **raises an exception in the case of an error**.
4. Three **predefined** streams are already open when the program starts:
   - `sys.stdin` – standard input;
   - `sys.stdout` – standard output;
   - `sys.stderr` – standard error output.
5. The `IOError` exception object, created when any file operations fails (including open operations), contains a property named `errno`, which contains the completion code of the failed action. Use this value to diagnose the problem.