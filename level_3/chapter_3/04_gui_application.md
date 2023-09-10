# A simple GUI application

## Building a GUI application from scratch
Now we're going to build a very simple and rather useless GUI application. Does that sound weird? Maybe, but the application, when ready, will make you more accustomed to some `tkinter` **habits** and **conventions**.

Our fabulous goal will look like the vision presented below:

<p align="center">
  <img src="images/app_1.png">
</p>

Are you ready? Let's start.

As everyone knows, Rome wasn't built in a day, and our application isn't an exception. We'll start with something absolutely **obvious** – we'll construct a window and launch an event controller – look at the code in the editor to see how to do it.
```python
import tkinter as tk

window = tk.Tk()
window.mainloop()
```
Our window looks like this one for now:

<p align="center">
  <img src="images/app_2.png">
</p>

There's nothing surprising yet. Let's add something to this dull gray area.

Our new friend is called `Label` – a non-clickable widget able to **present short textual information**, passed to the widget's constructor using a `text` argument. The text can later be changed at any moment of the widget's life.

As you can see, we're using the `pack()` geometry manager to compose the window.
```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(window, text = "Little label:")
label.pack()

window.mainloop()
```
Let's welcome `Label` into our window:

<p align="center">
  <img src="images/app_3.png">
</p>

Note: `pack()` resizes the window to a size large enough to fit all the packed widgets. This is its default behavior. Don't worry, the window will grow soon.

Our next companion will be `Frame`.

A `Frame` is another non-clickable component used to **group widgets** and to separate them (visually) from other window components. Our `Frame` plays a less important role – it just occupies a rectangle and fills it with its own color. We expect nothing more for now.

Let's check it out.
```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(window, text="Little label:")
label.pack()

frame = tk.Frame(window, height=30, width=100, bg="#000099")
frame.pack()

window.mainloop()
```
This is how the `Frame` manifests its presence:

<p align="center">
  <img src="images/app_4.png">
</p>

Make our window great again.

Now we invite a `Button` to join our team.

Our `Button` will be completely **mute**, as we haven’t bound anything to its command property. You can change that if you want.
```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(window, text="Little label:")
label.pack()

frame = tk.Frame(window, height=30, width=100, bg="#000099")
frame.pack()

button = tk.Button(window, text="Button")
button.pack(fill=tk.X)

window.mainloop()
```
This is what our window looks like now:

<p align="center">
  <img src="images/app_5.png">
</p>

Our next component is completely **invisible**. You won't find it in the window area.

It's the switch variable. Can't you see it? It's set to hold an object of the `IntVar` class. This object is designed to store **integer** values. "Okay," you may say, "can't we use a regular variable instead?"

**No, we can't**. Objects of the `IntVar` class are used by `tkinter` to **organize internal communication between different widgets**. A regular variable can't play such a role.

If you want such an object to store an integer value, you can't use the assignment operator. The class offers a dedicated method for that purpose, and the method is named `set()`.

Note: we've used the method to store a value of `1` inside the object.
```python
import tkinter as tk

window = tk.Tk()

label = tk.Label(window, text="Little label:")
label.pack()

frame = tk.Frame(window, height=30, width=100, bg="#000099")
frame.pack()

button = tk.Button(window, text="Button")
button.pack(fill=tk.X)

switch = tk.IntVar()
switch.set(1)

window.mainloop()
```
As the window's view hasn't changed, we can go directly to the next step.
