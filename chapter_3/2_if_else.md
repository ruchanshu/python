# Conditions and conditional execution

To make decisions, Python offers a special instruction. Due to its nature and its application, it's called a **conditional instruction** (or conditional statement).

The first form of a conditional statement, which you can see below is written very informally but figuratively:
```python
if true_or_not:
    do_this_if_true
```
This conditional statement consists of the following, strictly necessary, elements in this and this order only:
- the `if` keyword;
- one or more white spaces;
- an expression (a question or an answer) whose value will be interpreted solely in terms of `True` (when its value is non-zero) and `False` (when it is equal to zero);
- a `:` **colon** followed by a newline;
- an **indented** instruction or set of instructions (at least one instruction is absolutely required); the **indentation** may be achieved in two ways - by inserting a particular number of spaces (the recommendation is to use **four spaces of indentation**), or by using the tab character; note: if there is more than one instruction in the indented part, the indentation should be the same in all lines; even though it may look the same if you use tabs mixed with spaces, it's important to make all indentations **exactly the same** - Python 3 **does not allow mixing spaces and tabs** for indentation.

How does that statement work?

- If the `true_or_not` expression **represents the truth** (i.e., its value is not equal to zero), **the indented statement(s) will be executed**;
- if the `true_or_not` expression **does not represent the truth** (i.e., its value is equal to zero), **the indented statement(s) will be omitted** (ignored), and the next executed instruction will be the one after the original indentation level.

In real life, we often express a desire:

_if the weather is good, we'll go for a walk_

_then, we'll have lunch_


As you can see, having lunch is **not a conditional activity** and doesn't depend on the weather.
```python
if the_weather_is_good:
    go_for_a_walk()
have_lunch()
```

## Conditional execution: the if statement
**Conditionally executed statements have to be indented**. This creates a very legible structure, clearly demonstrating all possible execution paths in the code.
```python
if distance >= 1000:
    put_on_shoes()
    start_walk()
    have_fun()
have_lunch()
```
As you can see, put on shoes, start walking and having fun are all **executed conditionally** - when `distance` is more.

Having lunch is **always done** (i.e., the `have_lunch()` function is not indented and does not belong to the `if` block, which means it is always executed.)

## Conditional execution: the if-else statement

Now we know what we'll do **if the conditions are met**, and we know what we'll do **if not everything goes our way**. In other words, we have a "Plan B".

Python allows us to express such alternative plans using the _if-else_ statement:
```python
if true_or_false_condition:
    perform_if_condition_true
else:
    perform_if_condition_false
```
Thus, there is a new word: `else` - this is a **keyword**.

The part of the code which begins with `else` says what to do if the condition specified for the `if` is not met (note the **colon** after the word).

The _if-else_ execution goes as follows:

- if the condition evaluates to **True** (its value is not equal to zero), the `perform_if_condition_true` statement is executed, and the conditional statement comes to an end;
- if the condition evaluates to **False** (it is equal to zero), the `perform_if_condition_false` statement is executed, and the conditional statement comes to an end.

If the weather is good, we'll go for a walk. Otherwise, we'll go to a theatre. No matter if the weather is good or bad, we'll have lunch afterwards (after the walk or after going to the theatre).

Everything we've said about indentation works in the same manner inside **the else branch**:
```python
if the_weather_is_good:
    go_for_a_walk()
    have_fun()
else:
    go_to_a_theater()
    enjoy_the_movie()
have_lunch()
```

## Nested if-else statements
First, consider the case where the **instruction placed after the `if` is another `if`**.

Read what we have planned for this Sunday. If the weather is fine, we'll go for a walk. If we find a nice restaurant, we'll have lunch there. Otherwise, we'll eat a sandwich. If the weather is poor, we'll go to the theater. If there are no tickets, we'll go shopping in the nearest mall.

Let's write the same in Python. Consider carefully the code here:
```python
if the_weather_is_good:
    if nice_restaurant_is_found:
        have_lunch()
    else:
        eat_a_sandwich()
else:
    if tickets_are_available:
        go_to_the_theater()
    else:
        go_shopping()
```
Here are two important points:

- this use of the `if` statement is known as **nesting**; remember that every `else` refers to the `if` which lies **at the same indentation level**; you need to know this to determine how the ifs and elses pair up;
- consider how the **indentation improves readability**, and makes the code easier to understand and trace.

## The elif statement
Python keyword: `elif`. As you probably suspect, it's a shorter form of **else if**.

`elif` is used to **check more than just one condition**, and to **stop** when the first statement which is true is found.

Our next example resembles nesting, but the similarities are very slight. Again, we'll change our plans and express them as follows: If the weather is fine, we'll go for a walk, otherwise if we get tickets, we'll go to the theater, otherwise if there are free tables at the restaurant, we'll go for lunch; if all else fails, we'll return home and play chess.

Have you noticed how many times we've used the word _otherwise_? This is the stage where the `elif` keyword plays its role.
```python
if the_weather_is_good:
    go_for_a_walk()
elif tickets_are_available:
    go_to_the_theater()
elif table_is_available:
    go_for_lunch()
else:
    play_chess_at_home()
```

The way to assemble subsequent if-elif-else statements is sometimes called a **cascade**.

Some additional attention has to be paid in this case:
- you **mustn't use `else` without a preceding `if`**;
- `else` is always the **last branch of the cascade**, regardless of whether you've used `elif` or not;
- `else` is an **optional** part of the cascade, and may be omitted;
- if there is an else branch in the cascade, only one of all the branches is executed;
- if there is no else branch, it's possible that none of the available branches is executed.
