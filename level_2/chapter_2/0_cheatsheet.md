## Summary

### Characters and Strings vs. Computers
1. Computers store characters as numbers. There is more than one possible way of encoding characters, but only some of them gained worldwide popularity and are commonly used in IT: these are **ASCII** (used mainly to encode the Latin alphabet and some of its derivates) and **UNICODE** (able to encode virtually all alphabets being used by humans).
2. A number corresponding to a particular character is called a **codepoint**.
3. UNICODE uses different ways of encoding when it comes to storing the characters using files or computer memory: two of them are **UCS-4** and **UTF-8** (the latter is the most common as it wastes less memory space).

### The nature of strings in Python
1. Python strings are **immutable sequences** and can be indexed, sliced, and iterated like any other sequence, as well as being subject to the `in` and `not in` operators. There are two kinds of strings in Python:
   - **one-line** strings, which cannot cross line boundaries – we denote them using either apostrophes (`'string'`) or quotes (`"string"`)
   - **multi-line** strings, which occupy more than one line of source code, delimited by trigraphs:
      ```python
      '''
      string
      '''
      ```
      or
      ```python
      """
      string
      """
      ```

2. The length of a string is determined by the `len()` function. The escape character (`\`) is not counted. For example:
   ```python
   print(len("\n\n"))
   ```
   outputs `2`.

3. Strings can be **concatenated** using the `+` operator, and **replicated** using the `*` operator. For example:
   ```python
   asterisk = '*'
   plus = "+"
   decoration = (asterisk + plus) * 4 + asterisk
   print(decoration)
   ```
   outputs `*+*+*+*+*`.

4. The pair of functions `chr()` and `ord()` can be used to create a character using its codepoint, and to determine a codepoint corresponding to a character. Both of the following expressions are always true:
   ```python
   chr(ord(character)) == character
   ord(chr(codepoint)) == codepoint
   ```

5. Some other functions that can be applied to strings are:
   - `list()` – create a list consisting of all the string's characters;
   - `max()` – finds the character with the maximal codepoint;
   - `min()` – finds the character with the minimal codepoint.

6. The method named `index()` finds the index of a given substring inside the string.

### String methods
1. Some of the methods offered by strings are:
- `capitalize()` – changes all string letters to capitals;
- `center()` – centers the string inside the field of a known length;
- `count()` – counts the occurrences of a given character;
- `join()` – joins all items of a tuple/list into one string;
- `lower()` – converts all the string's letters into lower-case letters;
- `lstrip()` – removes the white characters from the beginning of the string;
- `replace()` – replaces a given substring with another;
- `rfind()` – finds a substring starting from the end of the string;
- `rstrip()` – removes the trailing white spaces from the end of the string;
- `split()` – splits the string into a substring using a given delimiter;
- `strip()` – removes the leading and trailing white spaces;
- `swapcase()` – swaps the letters' cases (lower to upper and vice versa)
- `title()` – makes the first letter in each word upper-case;
- `upper()` – converts all the string's letter into upper-case letters.

2. String content can be determined using the following methods (all of them return Boolean values):
- `endswith()` – does the string end with a given substring?
- `isalnum()` – does the string consist only of letters and digits?
- `isalpha()` – does the string consist only of letters?
- `islower()` – does the string consists only of lower-case letters?
- `isspace()` – does the string consists only of white spaces?
- `isupper()` – does the string consists only of upper-case letters?
- `startswith()` – does the string begin with a given substring?

### String in action
1. Strings can be compared to strings using general comparison operators, but comparing them to numbers gives no reasonable result, because **no string can be equal** to any number. For example:
   - `string == number` is always `False`;
   - `string != number` is always `True`;
   - `string >= number` always **raises an exception**.
2. Sorting lists of strings can be done by:
   - a function named `sorted()`, creating a new, sorted list;
   - a method named `sort()`, which sorts the _list in situ_
3. A number can be converted to a string using the `str()` function.
4. A string can be converted to a number (although not every string) using either the `int()` or `float()` function. The conversion fails if a string doesn't contain a valid number image (an exception is raised then).

### String Processing
1. Strings are key tools in modern data processing, as most useful data are actually strings. For example, using a web search engine (which seems quite trivial these days) utilizes extremely complex and complicated string processing, involving unimaginable amounts of data.
2. Comparing strings in a strict way (as Python does) can be very unsatisfactory when it comes to advanced searches (e.g. during extensive database queries). Responding to this demand, a number of _fuzzy_ string comparison algorithms has been created and implemented. These algorithms are able to find strings which aren't equal in the Python sense, but are **similar**.

   One such concept is the **Hamming distance**, which is used to determine the similarity of two strings. If this problem interests you, you can find out more about it here: https://en.wikipedia.org/wiki/Hamming_distance. Another solution of the same kind, but based on a different assumption, is the **Levenshtein distance** described here: https://en.wikipedia.org/wiki/Levenshtein_distance.

3. Another way of comparing strings is finding their _acoustic_ similarity, which means a process leading to determine if two strings sound similar (like "raise" and "race"). Such a similarity has to be established for every language (or even dialect) separately.

   An algorithm used to perform such a comparison for the English language is called **Soundex** and was invented – you won't believe – in 1918. You can find out more about it here: https://en.wikipedia.org/wiki/Soundex.

4. Due to limited native float and integer data precision, it's sometimes reasonable to store and process huge numeric values as strings. This is the technique Python uses when you force it to operate on an integer number consisting of a very large number of digits.

### More on Exceptions
1. An exception is an event during program execution caused by an abnormal situation. The exception should be handled to avoid the termination of the program. The part of your code that is suspected of being the source of the exception should be put inside the `try` branch.

   - When the exception happens, the execution of the code is not terminated, but instead jumps into the `except` branch. This is the place where the handling of the exception should take place. The general scheme for such a construction looks as follows:
   ```python
   :
   # The code that always runs smoothly.
   :
   try:
       :
       # Risky code.
       :
   except:
       :
       # Crisis management takes place here.
       : 
   :
   # Back to normal.
   :
   ```
2. If you need to handle more than one exception coming from the same `try` branch, you can add more than one `except` branch, but you have to label them with different exception names, like this:
   ```python
   :
   # The code that always runs smoothly.
   :
   try:
       :
       # Risky code.
       :
   except Except_1:
       # Crisis management takes place here.
   except Except_2:
       # We save the world here.
   :
   # Back to normal.
   :
   ```
   At most, one of the `except` branches is executed – none of the branches is performed when the raised exception doesn't match any of the specified exceptions.
3. You cannot add more than one anonymous (unnamed) `except` branch after the named ones.
   ```python
   :
   # The code that always runs smoothly.
   :
   try:
       :
       # Risky code.
       :
   except Except_1:
       # Crisis management takes place here.
   except Except_2:
       # We save the world here.
   except:
       # All other issues fall here.
   :
   # Back to normal.
   :
   ```
4. You cannot add more than one anonymous (unnamed) `except` branch after the named ones.
   ```python
   :
   # The code that always runs smoothly.
   :
   try:
       :
       # Risky code.
       :
   except Except_1:
       # Crisis management takes place here.
   except Except_2:
       # We save the world here.
   except:
       # All other issues fall here.
   :
   # Back to normal.
   :
   ```
5. All the predefined Python exceptions form a hierarchy, i.e. some of them are more general (the one named `BaseException` is the most general one) while others are more or less concrete (e.g. `IndexError` is more concrete than `LookupError`).
   - You shouldn't put more concrete exceptions before the more general ones inside the same `except` branch sequence. For example, you can do this:
   ```python
   try:
       # Risky code.
   except IndexError:
       # Taking care of mistreated lists
   except LookupError:
       # Dealing with other erroneous lookups
   ```
   but don't do that (unless you're absolutely sure that you want some part of your code to be useless)
   ```python
   try:
       # Risky code.
   except LookupError:
       # Dealing with erroneous lookups
   except IndexError:
       # You'll never get here
   ```
6. The Python statement `raise ExceptionName` can raise an exception on demand. The same statement, but lacking _ExceptionName_, can be used inside the `except` branch **only**, and raises the same exception which is currently being handled.
7. The Python statement `assert expression` evaluates the expression and raises the `AssertError` exception when the expression is equal to zero, an empty string, or None. You can use it to protect some critical parts of your code from devastating data.
8. Some abstract built-in Python exceptions are:
   - `ArithmeticError`,
   - `BaseException`,
   - `LookupError`.
9. Some concrete built-in Python exceptions are:
   - `AssertionError`,
   - `ImportError`,
   - `IndexError`,
   - `KeyboardInterrupt`,
   - `KeyError`,
   - `MemoryError`,
   - `OverflowError`.
