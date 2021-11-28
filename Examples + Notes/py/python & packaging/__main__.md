Most python code is either a module to be imported or a script that does something.

however, sometimes it is useful to make a file that can be both imported as a module and run as a script.

To do this, place script code inside **if **name** == "**main**"**.

This ensures that it won't be run if the file is imported.

```python
#i.e.
def function():
	print("This is a module function")

if __name__=="__main__":
	print("This is a script")
```

note: When the Python interpreter reads a source file, it executes all of the code it fines in the file. Before executing the code, it defines a few special variables.

For example, if the Python interpreter is running that module(the source file) as the main program, it sets the special **name** variable to have a value "**main**". If this file is being imported from another module, **name** will be set to the module's name.

If the code from the previous example is saved as a file called [sololearn.py](http://sololearn.py), it can then be imported to another script as a module, using the name sololearn.

```python
#sololearn.py
def function():
	print("This is a module function")

if __name__=="__main__":
	print("This is  a script")
```

```python
#some_script.py
import sololearn

sololearn.function()
```

```python
#result
>>>
This is a module function
>>>
```

what happens is that a custom module called sololearn has been created, and then used it in another script.