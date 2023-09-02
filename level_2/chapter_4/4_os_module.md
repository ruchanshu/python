# Introduction to the os module
In this section, you'll learn about a module called _os_, which lets you **interact with the operating system using Python**.

It provides functions that are available on Unix and/or Windows systems. If you're familiar with the command console, you'll see that some functions give the same results as the commands available on the operating systems.

A good example of this is the `mkdir` function, which allows you to create a directory just like the mkdir command in Unix and Windows. If you don't know this command, don't worry.

You'll soon have the opportunity to learn the functions of the os module, to perform operations on files and directories along with the corresponding commands.

In addition to file and directory operations, the os module enables you to:
- get information about the operating system;
- manage processes;
- operate on I/O streams using file descriptors.

### Getting information about the operating system
Before you create your first directory structure, you'll see how you can get information about the current operating system. This is really easy because the os module provides a function called _uname_, which returns an object containing the following attributes:
- **systemname** — stores the name of the operating system;
- **nodename** — stores the machine name on the network;
- **release** — stores the operating system release;
- **version** — stores the operating system version;
- **machine** — stores the hardware identifier, e.g., x86_64.

Let's look at how it is in practice:
```python
import os
print(os.uname())
```
Result:
```
posix.uname_result(sysname='Linux', nodename='192d19f04766', release='4.4.0-164-generic', version='#192-Ubuntu SMP Fri Sep 13 12:02:50 UTC 2019', machine='x86_64')
```
As you can see, the _uname_ function returns an object containing information about the operating system. The above code was launched on Ubuntu 16.04.6 LTS, so don't be surprised if you get a different result, because it depends on your operating system.

Unfortunately, the _uname_ function only works on some Unix systems. If you use Windows, you can use the _uname_ function in the _platform_ module, which returns a similar result.

The _os_ module allows you to quickly distinguish the operating system using the _name_ attribute, which supports one of the following names:
- **posix** — you'll get this name if you use Unix;
- **nt** — you'll get this name if you use Windows;
- **java** — you'll get this name if your code is written in Jython.

For Ubuntu 16.04.6 LTS, the name attribute returns the name _posix_:
```python
import os
print(os.name)
```
Result:
```
posix
```
**NOTE**: On Unix systems, there's a command called _uname_ that returns the same information (if you run it with the -a option) as the _uname_ function.

### Creating directories in Python
The _os_ module provides a function called _mkdir_, which, like the _mkdir_ command in Unix and Windows, allows you to create a directory. The _mkdir_ function requires a path that can be relative or absolute. Let's recall what both paths look like in practice:
- **my_first_directory** — this is a relative path which will create the _my_first_directory_ directory in the current working directory;
- **./my_first_directory** — this is a relative path that explicitly points to the current working directory. It has the same effect as the path above;
- **../my_first_directory** — this is a relative path that will create the _my_first_directory_ directory in the parent directory of the current working directory;
- **/python/my_first_directory** — this is the absolute path that will create the _my_first_directory_ directory, which in turn is in the _python_ directory in the root directory.

Look at the code in the editor. It shows an example of how to create the _my_first_directory_ directory using a relative path. This is the simplest variant of the relative path, which consists of passing only the directory name.
```python
import os

os.mkdir("my_first_directory")
print(os.listdir())
```
If you test your code here, it will output the newly created `['my_first_directory']` directory (and the entire content of the current working catalog).

The _mkdir_ function creates a directory in the specified path. Note that running the program twice will raise a `FileExistsError`.

This means that we cannot create a directory if it already exists. In addition to the path argument, the _mkdir_ function can optionally take the mode argument, which specifies directory permissions. However, on some systems, the mode argument is ignored.

To change the directory permissions, we recommend the chmod function, which works similarly to the chmod command on Unix systems. You can find more information about it in the documentation.

In the above example, another function provided by the os module named _listdir_ is used. The _listdir_ function returns a list containing the names of the files and directories that are in the path passed as an argument.

If no argument is passed to it, the current working directory will be used (as in the example above). It's important that the result of the _listdir_ function omits the entries '.' and '..', which are displayed, e.g., when using the ls -a command on Unix systems.

**NOTE**: In both Windows and Unix, there's a command called _mkdir_, which requires a directory path. The equivalent of the above code that creates the _my_first_directory_ directory is the `mkdir my_first_directory` command.

### Recursive directory creation
The `mkdir` function is very useful, but what if you need to create another directory in the directory you've just created. Of course, you can go to the created directory and create another directory inside it, but fortunately the os module provides a function called `makedirs`, which makes this task easier.

The `makedirs` function enables recursive directory creation, which means that all directories in the path will be created. Let's look at the code in the editor and see how it is in practice.
```python
import os

os.makedirs("my_first_directory/my_second_directory")
os.chdir("my_first_directory")
print(os.listdir())
```
The code should produce the following result:
```
['my_second_directory']
```
The code creates two directories. The first of them is created in the current working directory, while the second in the _my_first_directory_ directory.

You don't have to go to the _my_first_directory_ directory to create the _my_second_directory_ directory, because the `makedirs` function does this for you. In the example above, we go to the _my_first_directory_ directory to show that the `makedirs` command creates the _my_second_directory_ subdirectory.

To move between directories, you can use a function called `chdir`, which changes the current working directory to the specified path. As an argument, it takes any relative or absolute path. In our example, we pass the first directory name to it.

**NOTE**: The equivalent of the `makedirs` function on Unix systems is the mkdir command with the -p flag, while in Windows, simply the mkdir command with the path:

- Unix-like systems:

    `mkdir -p my_first_directory/my_second_directory`

- Windows:

    `mkdir my_first_directory/my_second_directory`

### Where am I now?
You already know how to create directories and how to move between them. Sometimes, when you have a really large directory structure that you navigate, you may not know which directory you're currently working in.

As you’ve probably guessed, the os module provides a function that returns information about the current working directory. It's called `getcwd`. Look at the code in the editor to see how to use it in practice.
```python
import os

os.makedirs("my_first_directory/my_second_directory")
os.chdir("my_first_directory")
print(os.getcwd())
os.chdir("my_second_directory")
print(os.getcwd())
```
Result:
```
.../my_first_directory
.../my_first_directory/my_second_directory
```
In the example, we create the _my_first_directory_ directory, and the _my_second_directory_ directory inside it. In the next step, we change the current working directory to the _my_first_directory_ directory, and then display the current working directory (first line of the result).

Next, we go to the _my_second_directory_ directory and again display the current working directory (second line of the result). As you can see, the `getcwd` function returns the absolute path to the directories.

**NOTE**: On Unix-like systems, the equivalent of the `getcwd` function is the _pwd_ command, which prints the name of the current working directory.

### Deleting directories in Python
The os module also allows you to delete directories. It gives you the option of deleting a single directory or a directory with its subdirectories. To delete a single directory, you can use a function called `rmdir`, which takes the path as its argument. Look at the code in the editor.
```python
import os

os.mkdir("my_first_directory")
print(os.listdir())
os.rmdir("my_first_directory")
print(os.listdir())
```
The above example is really simple. First, the _my_first_directory_ directory is created, and then it's removed using the `rmdir` function. The `listdir` function is used as proof that the directory has been removed successfully. In this case, it returns an empty list. When deleting a directory, make sure it exists and is empty, otherwise an exception will be raised.

To remove a directory and its subdirectories, you can use the `removedirs` function, which requires you to specify a path containing all directories that should be removed:
```python
import os

os.makedirs("my_first_directory/my_second_directory")
os.removedirs("my_first_directory/my_second_directory")
print(os.listdir())
```
As with the `rmdir` function, if one of the directories doesn't exist or isn't empty, an exception will be raised.

**NOTE**: In both Windows and Unix, there's a command called _rmdir_, which, just like the `rmdir` function, removes directories. What's more, both systems have commands to delete a directory and its contents. In Unix, this is the _rm_ command with the _-r_ flag.

### The `system()` function
All functions presented in this part of the course can be replaced by a function called _system_, which executes a command passed to it as a string.

The `system` function is available in both Windows and Unix. Depending on the system, it returns a different result.

In Windows, it returns the value returned by the shell after running the command given, while in Unix, it returns the exit status of the process.

Let's look at the code and see how it is in practice.
```python
import os

returned_value = os.system("mkdir my_first_directory")
print(returned_value)
```
Result:
```
0
```
The above example will work in both Windows and Unix. In our case, we receive exit status `0`, which indicates success on Unix systems.

This means that the _my_first_directory_ directory has been created. As part of the exercise, try to list the contents of the directory where you created the _my_first_directory_ directory.
