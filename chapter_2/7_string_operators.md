# String operators
It's time to return to these two arithmetic operators: `+` and `*`.

## Concatenation
The `+` (plus) sign, when applied to two strings, becomes a **concatenation operator**:
```python
string + string
```

It simply **concatenates** (glues) two strings into one. Of course, like its arithmetic sibling, it can be used more than once in one expression, and in such a context it behaves according to left-sided binding.

In contrast to its arithmetic sibling, the concatenation operator is **not commutative**, i.e., `"ab" + "ba"` is not the same as `"ba" + "ab"`.

Don't forget - if you want the `+` sign to be a **concatenator**, not an adder, you must ensure that **both its arguments are strings**.

You cannot mix types here.

> [!NOTE]
> using `+` to concatenate strings lets you construct the output in a more precise way than with a pure `print()` function, even if enriched with the `end=` and `sep=` keyword arguments.

## Replication
The `*` (asterisk) sign, when applied to a string and number (or a number and string, as it remains commutative in this position) becomes a **replication operator**:
```python
string * number
number * string
```
It replicates the string the same number of times specified by the number.

For example:
- `"James" * 3` gives `JamesJamesJames`
- `3 * "an"` gives `ananan`
- `5 * "2"` (or `"2" * 5`) gives `22222` (not `10`!)

> [!IMPORTANT]
> A number less than or equal to zero produces an **empty string**.

This simple program "draws" a rectangle, making use of an old operator (`+`) in a new role:
```python
print("+" + 10 * "-" + "+")
print(("|" + " " * 10 + "|\n") * 5, end="")
print("+" + 10 * "-" + "+")
```