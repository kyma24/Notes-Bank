very similar to lists, except that they are immutable(can't be changed)

also, they are created using parentheses rather than square brackets

```python
words = ("spam", "eggs", "sausages",)

#can access values in the tuple with their index, just as with lists
print(words[0])

#trying to reassign a value in a tuple causes a TypeError
words[1] = "cheese"
```

note: and just like w/ lists & dictionaries, tuples can be nested within each other

tuples can be created w/o the parentheses by just separating the values w/ commas

```python
my_tuple = "one", "two", "three"
print(my_tuple[0])
```

```python
#empty tuples are created using empty parentheses pair
tpl = ()
```

note: tuples are faster than lists, but the downside is that they can't be changed


-   tuple unpacking
    
    this allows you to assign each item in a collection to a variable.
    
    ```python
    #i.e.
    numbers = (1, 2, 3)
    a, b, c = numbers
    print(a)
    print(b)
    print(c)
    ```
    
    note: can also be used to swap variables by doing **a, b = b, a**, since b, a on the right hand side forms the tuple (b,a) which is then unpacked.
    
    a variable that is prefaced with an asterisk(\*) takes all values from the collection that are left over from the other variables.
    
    ```python
    #i.e.
    a, b, *c, d = [1, 2, 3, 4, 5, 6, 7, 8, 9]
    print(a)
    print(b)
    print(c)
    print(d)
    
    #note: c will get assigned the values 3 to 8
    ```