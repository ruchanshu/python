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

### Processing files
1. To read a file’s contents, the following stream methods can be used:
   - `read(number)` – reads the `number` characters/bytes from the file and returns them as a string; is able to read the whole file at once;
   - `readline()` – reads a single line from the text file;
   - `readlines(number)` – reads the `number` lines from the text file; is able to read all lines at once;
   - `readinto(bytearray)` – reads the bytes from the file and fills the `bytearray` with them;
2. To write new content into a file, the following stream methods can be used:
   - `write(string)` – writes a `string` to a text file;
   - `write(bytearray)` – writes all the bytes of `bytearray` to a file;
3. The `open()` method returns an iterable object which can be used to iterate through all the file's lines inside a `for` loop. For example:
   ```python
   for line in open("file", "rt"):
       print(line, end='')
   ```
   The code copies the file's contents to the console, line by line. **Note**: the stream closes itself **automatically** when it reaches the end of the file.

### OS Module
1. The `uname` function returns an object that contains information about the current operating system. The object has the following attributes:
   - `systemname` (stores the name of the operating system)
   - `nodename` (stores the machine name on the network)
   - `release` (stores the operating system release)
   - `version` (stores the operating system version)
   - `machine` (stores the hardware identifier, e.g. x86_64.)
2. The _name_ attribute available in the _os_ module allows you to distinguish the operating system. It returns one of the following three values:
   - **posix** (you'll get this name if you use Unix)
   - **nt** (you'll get this name if you use Windows)
   - **java** (you'll get this name if your code is written in something like Jython)
3. The `mkdir` function creates a directory in the path passed as its argument. The path can be either relative or absolute, e.g:
   ```python
   import os
   
   os.mkdir("hello") # the relative path
   os.mkdir("/home/python/hello") # the absolute path
   ```
   **Note**: If the directory exists, a `FileExistsError` exception will be thrown. In addition to the `mkdir` function, the `os` module provides the `makedirs` function, which allows you to recursively create all directories in a path.
4. The result of the `listdir()` function is a list containing the names of the files and directories that are in the path passed as its argument.

   It's important to remember that the `listdir` function omits the entries '.' and '..', which are displayed, for example, when using the `ls -a` command on Unix systems. If the path isn't passed, the result will be returned for the current working directory.

5. To move between directories, you can use a function called `chdir()`, which changes the current working directory to the specified path. As its argument, it takes any relative or absolute path.

   If you want to find out what the current working directory is, you can use the `getcwd()` function, which returns the path to it.

6. To remove a directory, you can use the `rmdir()` function, but to remove a directory and its subdirectories, use the `removedirs()` function.

7. On both Unix and Windows, you can use the system function, which executes a command passed to it as a string, e.g.:
   ```python
   import os
   
   returned_value = os.system("mkdir hello")
   ```
   The system function on Windows returns the value returned by shell after running the command given, while on Unix it returns the exit status of the process.

